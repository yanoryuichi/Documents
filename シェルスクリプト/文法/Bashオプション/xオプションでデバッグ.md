# xオプションでデバッグ

こんなスクリプト test.sh があったとして、

```bash
#!/bin/bash

dir="/home/taro/tmp/"
files=$(ls -1 $dir);
IFS='
'
for f in $files; do
    echo "FILE: " $f
done
```

xオプションを付けてスクリプトを実行すると、

```bash
$ bash -x test.sh
```

変数の中身が確認できる。

```bash
+ dir=/home/taro/tmp/
++ ls -1 /home/taro/tmp/
+ files='1.txt
2.txt
3.txt'
+ IFS='
'
+ for f in '$files'
+ echo 'FILE: ' 1.txt
FILE:  1.txt
+ for f in '$files'
+ echo 'FILE: ' 2.txt
FILE:  2.txt
+ for f in '$files'
+ echo 'FILE: ' 3.txt
FILE:  3.txt
```
