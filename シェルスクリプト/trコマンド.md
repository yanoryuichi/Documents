# trコマンド

## 小文字を大文字へ変換

```bash
echo 'foo' | tr 'a-z' 'A-Z'
```

```bash
FOO
```

## 改行コードを変換

```bash
tr '\r' '\n' < cr.txt > lf.txt
```

「CR」から「LF」へ。

## 連続した改行を削除

```bash
cat 1.txt
```

```bash
1 
 

2
3
```

```bash
tr -s '\n' < 1.txt
```

```bash
1
2
3
```

## 文字を削除

```bash
echo 'foo bar baz' | tr -d 'ab'
```

```bash
foo r z
```
