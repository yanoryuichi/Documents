# 格納されたデータの文字コードを調べる (strtohex関数)

格納されたデータの文字コード等を調べるのに使う。以下READMEより。

> 1. strtohexとは
>
>   strtohexは引数の文字列を16進表現にしたものをTEXTとして返します．
>   strtohexは文字化けそのほかのトラブルの解析の役に立つ(かもしれません)

## パッチ
PostgreSQL8.3でコンパイル出来なかったので。

```clike
$ diff strtohex.c.orig strtohex.c
29a30,37
> #ifndef SET_VARSIZE
> #define SET_VARSIZE(v,l) (VARATT_SIZEP(v) = (l))
> #endif
> #ifdef PG_MODULE_MAGIC
> PG_MODULE_MAGIC;
> #endif
>
>
57c65
<       VARATT_SIZEP(result) = len + VARHDRSZ;
---
>     SET_VARSIZE(result,len + VARHDRSZ);
```

## 使い方

```clike
SELECT * FROM member WHERE strtohex(namae) LIKE '%a525%'; 
```

0xa525：リストア時に警告表示される不正な文字列のコード

## 参考
http://ml.postgresql.jp/pipermail/pgsql-jp/2004-January/015488.html
#ref(strtohex-1.0.tar.gz)
