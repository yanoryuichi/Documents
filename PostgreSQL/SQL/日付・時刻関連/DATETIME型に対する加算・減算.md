# DATETIME型に対する加算・減算

## 加算・減算
PostgreSQLではDATETIME型に対する加算を以下のように演算子+とInterval型を使って行う。

```clike
SELECT now() + interval '3 months';
```

上の3を数値型で渡したい場合、以下のように文字列連結した後にinterval型にキャストする。

```clike
SELECT now() + CAST( 3 || ' months' AS interval );
```

## 参考

日付/時刻関数と演算子 
: http://www.postgresql.jp/document/9.3/html/functions-datetime.html

Interval型 
: http://www.postgresql.jp/document/9.1/html/datatype-datetime.html#DATATYPE-INTERVAL-INPUT
