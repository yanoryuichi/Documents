# PWD2

pwdコマンドを加工して、今いるディレクトリとその上のディレクトリのみ表示する。

```bash
function pwd2() {
   local _ifs=IFS
   local buf=''
   local dir=()
   local n=0
   local idx=0
   IFS=/
   for i in $PWD; do
       n=${#dir[@]}
       dir[$n]=$i
   done
   n=${#dir[@]}
   for i in 3 2 1; do
       idx=$((n-$i))
       if [ "$idx" -gt 0 ]; then
           buf=$buf/${dir[$idx]}
       fi
   done
   if [ "$n" -gt 2 ]; then
       buf=${buf#/}
   fi
   IFS=$_ifs
   echo $buf
}
```
