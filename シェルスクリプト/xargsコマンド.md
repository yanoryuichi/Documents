# xargsコマンド

### xargs 引数なし（デリミタはデフォルトでスペース・タブ・改行）

```bash
$ echo "/etc/passwd
/etc/hosts
/etc/resolv.conf" | xargs wc -l

 28 /etc/passwd
  1 /etc/hosts
  3 /etc/resolv.conf
 32 合計
```

```bash
$ echo "/etc/passwd /etc/hosts /etc/resolv.conf" | xargs wc -l

 28 /etc/passwd
  1 /etc/hosts
  3 /etc/resolv.conf
 32 合計
```

### xargs -d デリミタ指定

```bash
# デリミタにスペースを指定
$ echo -n "/etc/passwd /etc/hosts /etc/resolv.conf" | xargs -d " " wc -l

 28 /etc/passwd
  1 /etc/hosts
  3 /etc/resolv.conf
 32 合計
```

```bash
# デリミタに改行を指定
$ echo "/etc/passwd
/etc/hosts
/etc/resolv.conf" | xargs -d "\n" wc -l

 28 /etc/passwd
  1 /etc/hosts
  3 /etc/resolv.conf
 32 合計
```

### xargs -I {} 引数を展開

```bash
$ echo -n /etc/passwd /etc/hosts /etc/resolv.conf | xargs -d " " -I {} wc -l {}

 28 /etc/passwd
 1 /etc/hosts
 3 /etc/resolv.conf
```

オプション-Iを付けない場合は、

```bash
wc -l /etc/passwd /etc/hosts /etc/resolv.conf
```

が実行されるのに対し、-Iを付けると

```bash
wc -l /etc/passwd
wc -l /etc/hosts
wc -l /etc/resolv.conf
```

のように3回wcコマンドが実行される。{}で引数を展開できるので、


```bash
$ ls *.txt
1.txt  2.txt  3.txt

$ ls -1 *.txt | xargs -I {} cp {} {}.backup

$ ls *
1.txt  1.txt.backup  2.txt  2.txt.backup  3.txt  3.txt.backup
```

のようなことが可能になる。
