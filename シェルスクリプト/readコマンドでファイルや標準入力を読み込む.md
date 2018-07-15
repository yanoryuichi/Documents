# readコマンドでファイルや標準入力を読み込む

## ファイルを読み込む

```bash
while read line; do
echo $line
done < file.txt
```

## CSVファイルを読み込む

```bash
$ cat 1.csv
a,b,c
x,y,z
```

```bash
$ while IFS=, read col1 col2 col3; do echo "$col1-$col2-$col3"; done < ./1.csv
a-b-c
x-y-z
```

## findコマンドの結果を標準入力を介して読み込む

```bash
$ ls
1.txt  2.txt  3.txt
```

```bash
$ find . -print0 | while read -d $'\0' f; do echo "DEBUG: $f"; done
DEBUG: .
DEBUG: ./3.txt
DEBUG: ./2.txt
DEBUG: ./1.txt
```

findコマンドの"-print0"は区切り文字をヌル文字にするオプション。
