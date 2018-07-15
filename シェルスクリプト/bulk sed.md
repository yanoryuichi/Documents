# bulk sed

```bash
#!/bin/sh

# ============================================================================
# 一括置換スクリプト
# ============================================================================

# ----------------------------------------------------------------------------
# 初期設定
# ----------------------------------------------------------------------------

# 置換したファイルを出力するディレクトリ
save_dir=/tmp/save
# 置換する文字列（置換前文字列 置換後文字列）
texts='
test TEST
sample Sample
'

# ----------------------------------------------------------------------------
# メイン
# ----------------------------------------------------------------------------
IFS='
'

if [ "$1" = "-debug" ]; then
  debug=1
  shift
elif [ "$1" = "-echo" ]; then
  echo=1
  shift
fi

# saveディレクトリを削除しておく
if [ -e $save_dir ]; then
    rm -rf $save_dir
fi
if [ ! -d $save_dir ]; then
    mkdir -p $save_dir
fi

# 引数からfind コマンドの対象ディレクトリを組み立てる
target_dir=`pwd`
target_dir=`echo $target_dir/$1 | sed -e 's/\/$//'`
esc_target_dir=`echo $target_dir | sed -e 's/\//\\\\\//g'`
if [ ! -d $target_dir ]; then
  echo "usage: $0 [ -debug | -echo ] DIR"    
  exit 1
fi

# tmpディレクトリを作り、対象ディレクトリ以下のファイルをコピーする
tmp_dir=/tmp/tmp
esc_tmp_dir=`echo $tmp_dir/ | sed -e 's/\//\\\\\//g'`
if [ -e $tmp_dir ]; then
    rm -rf $tmp_dir
fi
if [ ! -d $tmp_dir ]; then
    mkdir -p $tmp_dir
fi
cp -a $target_dir/* $tmp_dir/

# findを実行して対象のファイルを抽出する
tmp_files=`find $tmp_dir ! -path '*.svn*' -type f`

echo -n "wait"
for text in $texts; do
  echo -n "."
  # 置換文字列を組み立てる
  text1=`echo $text | cut -f 1 -d ' '`
  text2=`echo $text | cut -f 2 -d ' '`
  for tmp_file in $tmp_files; do
    # grepしてsedすべきか調べる
    if grep "$text1" $tmp_file >/dev/null; then
      if [ "$debug" ]; then
        grep "$text1" $tmp_file /dev/null
        continue
      fi
      # 出力するファイルのパスを作る
      # パス中のディレクトリがなければここで作る
      save_path=`echo $tmp_file | sed -e s/^$esc_tmp_dir//`
      d=`dirname $save_dir/$save_path`
      if [ ! -e $d ]; then
        mkdir -p $d
      fi
      # sedを実行
      if [ "$echo" ]; then
        echo sed -e \"s/$text1/$text2/g\" $tmp_file \> $save_dir/$save_path
        echo cp $save_dir/$save_path $tmp_file
      else
        sed -e "s/$text1/$text2/g" $tmp_file > $save_dir/$save_path
        cp $save_dir/$save_path $tmp_file
      fi
    fi
  done
done

if [ ! "$echo" ]; then
  echo
  echo "done. saved to: $save_dir"
  rm -rf $tmp_dir
fi
```
