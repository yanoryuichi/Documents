# sedコマンド

## パターン
### 量指定・後方参照

量指定
: \{N\}

後方参照
: /\(.*\)/\1/

7桁郵便番号1234567をハイフンを差し込んで123-4567に。

```bash
echo "1234567" | sed -e 's/\(.\{3\}\)\(.\{4\}\)/\1-\2/'
```

## 置換
### 複数置換する

```bash
sed -e 's/H/h/g' -e 's/O/o/g' 1.txt
```

```bash
hELLo
WoRLD
```

eオプションを重ねる。または、

```bash
sed -e 's/H/h/g; s/O/o/g' 1.txt
```

「;」でつなぐ。

### 後方参照
対象を「\(\)」でくるみ、「\1」で参照する。

```bash
echo abc | sed 's/a\(.\)c/\1/'
```

```bash
=> b
```

### マッチした文字列を挿入する
「&」を使う。

```bash
echo abc | sed 's/a/&XYZ/'
```

```bash
=> aXYZbc
```

```bash
echo abc | sed 's/.*/&XYZ/'
```

```bash
=> abcXYZ
```

### 行末に文字列を挿入する

```bash
sed -e 's/$/ END/' 1.txt
```

```bash
HELLO END
WORLD END
```

### マッチした行の間にある全ての行に対して置換する

```bash
sed '/TWO/,/FOUR/s/^/#/' 1.txt
```

```bash
ONE
#TWO
#THREE
#FOUR
FIVE
```

「TWO」から「FOUR」までの行に対してs/^/#/を実行する。

### ファイルの先頭行に文字列を挿入する

```bash
sed '1s/^/abc\n/' 1.txt
```

## 検索・抽出
### マッチした行だけを表示する

```bash
sed -n '/abc/p' 1.txt
```

sedコマンドは-nオプションを付けないとファイルの全内容を表示する。ので、↑の場合、nオプション無しだと二重に表示される。ので、nオプションを付ける。

### マッチした行を除外する

```bash
sed '/abc/d' 1.txt
```

### 指定した行番号の行を除外する（N,Md）

```bash
cat 1.txt
```

```bash
=> 01
   02
   03
   04
```

```bash
sed '2,3d' 1.txt
```

```bash
=> 01
   04
```

```bash
sed '2,$d' 1.txt
```

```bash
=> 01
```

### 最初にマッチした行だけ置換する（0,/REGEXP/s/foo/Bar/）

```bash
cat 1.txt

abc
122
def
234
```

```bash
sed -e '0,/2/s/2/X/' 1.txt

abc
1X2
def
234
```

「0,/REGEXP/」で行を指定した後に（REGEXPはここでは「2」）、「s/2/X/」で2をXに置換すると、4行目の「234」の「2」は置換されない。

### シェバングの置換（1行目のみ）

```bash
cat 1.pl | sed -e '1s#/usr/bin/perl#/usr/local/bin/perl#'
```

## 参考になるサイト

- http://www.grymoire.com/Unix/Sed.html
- http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_05_02.html#sect_05_02_01
- http://users.cybercity.dk/~bse26236/batutil/help/SED.HTM#11.20
- http://www.linuxtopia.org/online_books/linux_tool_guides/the_sed_faq/sedfaq4_004.html
