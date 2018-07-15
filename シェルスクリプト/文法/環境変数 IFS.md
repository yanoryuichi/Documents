# 環境変数 IFS

## 設定する

```bash
IFS='
'
```

または

```bash
IFS=$(echo -en "\n")
```

または

```bash
IFS=$'\n'
```

### $'string'について
bashのmanのクォート (quoting)の項を参考にする。 http://linuxjm.sourceforge.jp/html/GNU_bash/man1/bash.1.html#lbAQ

## デフォルトの設定

```bash
IFS="$'\n'$'\t' "
```

## 設定の確認

```bash
$ echo $IFS | od -a
0000000  nl
0000001
```

## 使用例
以下のような3行からなるテキストファイルtxtがあるとする。

```bash
$ cat txt
123
4 56
7 8 9
```

### IFSに改行タブスペースを設定した場合

```bash
$ IFS=$'\n\t '; for i in $(cat txt); do echo "DEBUG: " $i; done
DEBUG:  123
DEBUG:  4
DEBUG:  56
DEBUG:  7
DEBUG:  8
DEBUG:  9
```

### IFSに改行のみを設定した場合

```bash
$ IFS=$'\n'; for i in $(cat txt); do echo "DEBUG: " $i; done
DEBUG:  123
DEBUG:  4 56
DEBUG:  7 8 9
```

### IFSにスペースのみを設定した場合

```bash
$ IFS=$' ' ; for i in $(cat txt); do echo "DEBUG: " $i; done
DEBUG:  123
4
DEBUG:  56
7
DEBUG:  8
DEBUG:  9
```
