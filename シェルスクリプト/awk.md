# awk

## 文字列中のシングルクォートの表示

```bash
awk "BEGIN { print \"That's it\" }"
  => That's it
```

```bash
awk 'BEGIN { print "That\'s it" }'
  => 間違い
```

シェルのエスケープの性格上、ワンライナーでシングルクォートを表示する場合は上の例のようにする。

## セパレータを指定して取り出す

```bash
echo 'a,b,c' | awk -F , '{print $2}'
  => b
```

もしくは

```bash
echo 'a,b,c' | awk 'BEGIN{FS=","} {print $2}'
  => b
```

## ENDブロック

```bash
ps -e -o vsz,cmd | grep httpd | awk '{sum+=$1} END {print sum}'
  => 1871064
```

全行処理後に合計メモリを表示。

## print 関数

```bash
echo 'a,b,c' | awk 'BEGIN{FS=","} { print "DEBUG: " $1 " & " $2 }'
  => DEBUG: a & b
```

文字列連結はスペース区切りで文字列や変数を列挙する。

## printf 関数

```bash
echo 'a,b,1' | awk 'BEGIN{FS=","} { printf( "DEBUG: %s & %d\n", $1, $3 ) }'
  => DEBUG: a & 1
```

printf()は改行が付かないので、自分で改行を付ける。

## 正規表現で行をフィルタする

```bash
ifconfig eth0 | awk '/inet addr:/ {print $2}' | sed -e 's/addr://'
```

## 後方参照

```bash
ifconfig eth0 | grep "inet addr:" | awk '{print gensub(/^.*inet addr:([^ ]+).*$/, "\\1", 1)}'
```

getnsub()を使う。

### Perlを使う場合

```bash
ifconfig eth0 | perl -ne 'print $1 . "\n" if /inet addr:(\S+)/'
```
