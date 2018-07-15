# grepコマンド

## OR検索

```bash
ls | grep -e '.html' -e '.css' # .htmlと.cssだけ
ls | grep -E '.html|.css'      # .htmlと.cssだけ（拡張正規表現を使って）
```

## AND検索

```bash
ls -l | grep 2016 | grep .txt
```

## NOT検索

```bash
ls | grep -v '.html'               # .html以外
ls | grep -v -e '.html' -e '.css'  # .htmlと.css以外
ls | grep -v -E '.html|.css'       # .htmlと.css以外（拡張正規表現を使って）
```

## マッチしたファイル名だけ取り出す

```bash
grep -l FOO *
```

## マッチした内容だけ取り出す（ファイル名を抑止する）

```bash
grep -h FOO *
```

## マッチした行数を調べる

```bash
grep -c FOO *
```

```bash
1.txt:1
2.txt:0
3.txt:1
```

## 独立した単語として検索する

```bash
cat 1.txt
```

```bash
FOOBAR
BAZ FOO
```

```bash
grep -w FOO 1.txt
```

```bash
BAZ FOO
```

## マッチした前後の行を表示する

```bash
cat 1.txt
```

```bash
01
02
03
04 FOO
05
06
07
```

```bash
grep -A2 -B1 FOO 1.txt
```

```bash
03
04 FOO
05
06
```

## 再帰的に指定したファイルのみgrepする

```bash
(IFS=$'\n'; for f in $(find . -type f); do (file $f | grep "FOO_BAR_BAZ") && echo $f ; done)
```
