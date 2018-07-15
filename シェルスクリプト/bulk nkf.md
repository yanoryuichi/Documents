# bulk nkf

改行コードを一括で置換する。

## 使い方
引数に一括置換したいファイルのあるディレクトリを指定すると、/tmp/save以下に全ファイルのコピーができる。その際、テキストファイルの場合、nkfが実行される。

```bash
bulk-nkf.sh ./foo
ls /tmp/save/foo
```


subversionファイルは省いてあるので、必要であればrsyncで元のファイルを上書きすればよい。

```bash
rsync -avz /tmp/save/foo /home/user/foo
```

## 気になったこと
nkfコマンドはDOSの改行コードのファイルを読むときに文字コードの判定を失敗するようだ。nkf -E -eで文字コードを明示してあげた。

```bash
#!/bin/sh

save_dir=/tmp/save

target_dir=$1
if [ ! -d "$target_dir" ]; then
    echo "error: no such directory: $target_dir"
    exit 1
fi

if [ -e $save_dir ]; then
    rm -rf $save_dir
fi
mkdir $save_dir

files=`find $target_dir -type f ! -path '*svn*'`
for f in $files; do
    d=`dirname $f`
    if [ ! -e $save_dir/$d ]; then
        mkdir -p $save_dir/$d
    fi
    is_text=
    if file $f | grep "text" >/dev/null; then
        is_text=1
    fi
    if [ "$is_text" ]; then
        nkf -E -e -d $f > $save_dir/$f
    else
        cp $f $save_dir/$f
    fi
done
```
