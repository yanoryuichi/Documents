#diff2

あるプロジェクトとあるプロジェクト以下のディレクトリ・ファイルについて、再帰的なdiffを取る。

想定するのは、テスト環境から本番環境へファイルをコピー（本番反映）する場合に、テスト環境のディレクトリ以下と本番環境のディレクトリ以下の差分を取りたい場合など。

```bash
#!/bin/sh

# ------------------------------------------------------------------------------
# Configuration
# ------------------------------------------------------------------------------
EXCLUDES="
C/A
" 
# ------------------------------------------------------------------------------
# Parse Arguments
# ------------------------------------------------------------------------------
uid=`id -u`
date=`date +%Y%m%d`
tmp_base=/tmp/.diff2.tmp.$uid
tmp_file=$tmp_base.$date
case $1 in
    -ignore|-i)
    echo $2 >> $tmp_file
    exit
    ;;
  -show|-s)
    if [ -f $tmp_file ]; then
      cat $tmp_file
    fi
    exit
    ;;
  -clear|-c)
    if [ -f $tmp_file ]; then
      rm -f $tmp_base.*
    fi
    exit
    ;;
  -rm)
    RM=1
    shift
    ;;
  -cp)
    CP=1
    shift
    ;;
esac
if [ -f $tmp_file ]; then
  exc=`cat $tmp_file`
  EXCLUDES="$EXCLUDES$exc"
fi

# ----------------------------------
# Check two directories in arguments
# ----------------------------------
idx=1
for arg in $*; do
  if [ -d $arg ]; then
    eval DIR$idx=$arg
    idx=`expr $idx + 1`
  elif [ -f $arg ]; then
    eval FILE$idx=$arg
    idx=`expr $idx + 1`
  elif [ -f $DIR1/$arg -a -f $DIR2/$arg ]; then
    FILE0=$arg
  else
    ARGS="$ARGS $arg"
  fi
done

# Remove the last '/' if exists
# /foo/var/ => /foo/var 
if [ -d "$DIR1" ];then
  DIR1=`echo "$DIR1"  | sed -e 's/\/$//'`
fi
if [ -d "$DIR2" ];then
  DIR2=`echo "$DIR2"  | sed -e 's/\/$//'`
fi

err=1
if [ "$DIR1" != '' -a "$DIR2" != '' ]; then
  err=
fi
if [ "$FILE1" != '' -a "$FILE2" != '' ]; then
  err=
fi
if [ "$CP" -o "$RM" ]; then
  if [ "$DIR1" = '' -o "$DIR2" = '' ]; then
    err=1
  fi
fi
if [ $err ]; then
  echo "----------------------------"
  echo " USAGE"
  echo "----------------------------"
  echo "DO DIFF"
  echo "$0 DIR1 DIR2              or"
  echo "$0 FILE1 FILE2            or"
  echo "$0 DIR1 DIR2 COMMON_FILE"
  echo 
  echo "SET/UNSET IGNORE FILES"
  echo "$0 -ignore DIR|FILE       or"
  echo "$0 -show                  or"
  echo "$0 -clear                 or"
  echo 
  echo "ECHO CP COMMAND"
  echo "$0 -cp DIR1 DIR2"
  echo 
  echo "ECHO RM COMMAND"
  echo "$0 -rm DIR1 DIR2"
  exit 1
fi

# ------------------------------------------------------------------------------
# Do diff for files (not direcotries) and EXIT
# ------------------------------------------------------------------------------
if [ "$FILE0" ]; then
  diff $ARGS "$DIR1/$FILE0" "$DIR2/$FILE0"
  exit
elif [ "$FILE1" != '' -a "$FILE2" != '' ]; then
  diff $ARGS $FILE1 $FILE2
  exit
fi

# ------------------------------------------------------------------------------
# Do diff for direcotries
# ------------------------------------------------------------------------------
DIFF=`LC_ALL=C diff -r -q $ARGS $DIR1 $DIR2`

IFS="
"
for diff in $DIFF; do

# ------------
# Only in DIR1
# ------------
  DIR1_=`echo $DIR1 | sed -e 's/\//\\\\\//g'`
  DIR2_=`echo $DIR2 | sed -e 's/\//\\\\\//g'`
  if echo $diff | grep "Only in $DIR1_" 2>&1 1>/dev/null; then
    dir=`echo $diff | cut -f 3 -d ' ' | sed -e "s/$DIR1_//" | tr ':' '/'`
    file=`echo $diff | cut -f 4 -d ' '`
    mesg="<-- :"

# ------------
# Only in DIR2
# ------------
  elif echo $diff | grep "Only in $DIR2" 2>&1 1>/dev/null; then
    dir=`echo $diff | cut -f 3 -d ' ' | sed -e "s/$DIR2_//" | tr ':' '/'`
    file=`echo $diff | cut -f 4 -d ' '`
    mesg="--> :"

# ---------
# Different
# ---------
  else
    dir=
    file=`echo $diff | cut -f 2 -d ' ' | sed -e "s/$DIR1_//"`
    mesg=" *  :"
  fi

  dir=`echo $dir | sed -e 's/^\///'`
  file=`echo $file | sed -e 's/^\///'`

# ---------------------------------------
# Check where the file is excluded or not
# If so, skip
# ---------------------------------------
  show=1
  for e in $EXCLUDES; do
    if echo "$dir$file" | grep -E "$e" 2>&1 1>/dev/null; then
      show=
      break
    fi
  done

# -----------------------
# Show the result of DIFF
# -----------------------
if [ $show ]; then
  if [ $CP ]; then
    if [ $mesg = '<-- :' -o $mesg = ' *  :' ]; then
    echo cp $DIR1/$dir$file $DIR2/$dir$file
    fi
  elif [ $RM ]; then
    if [ $mesg = '--> :' ]; then
    echo rm $DIR2/$dir$file
    fi
  else
  echo $mesg $dir$file
  fi
fi
done
# vim: sw=2:
```
