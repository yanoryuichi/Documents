# SSL接続

## インストール
configure時に--with-opensslオプションを指定してコンパイルする。

## 設定
### postgresql.conf

```clike
ssl=on
```

## 証明書の作成
PGDATA以下にopensslコマンドで作成したserver.crtとserver.keyを置く。

## 参考

- http://vibhorkumar.wordpress.com/2011/07/17/how-to-enable-ssl-in-postgresqlppas/
- http://www.postgresql.org/docs/8.4/static/ssl-tcp.html
