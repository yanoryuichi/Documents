# mod_access



## チュートリアル
http://httpd.apache.org/docs/2.0/howto/auth.html

## 指定した接続元IPアドレスからのみ

```clike
<Directory /var/www/html>
    Order deny,allow
    Deny from All
    Allow from 192.168.99.99
</Directory>
```

## ベーシック認証をかけたディレクトリの中のサブディレクトリを公開する
まず、/var/www/htdocs以下にベーシック認証をかける。

```clike
<Directory /var/www/htdocs/>
  Require valid-user
  AuthType Basic
  AuthUserFile "/var/www/.htpasswd"
  AuthName "KEEP-OUT"
</Directory>
```

次に、/var/www/htdocs/publicディレクトリを公開する。mod_accessですべてのホストからのアクセスをOKとし、Satisfyでベーシック認証の効果をなくす。

```clike
<Directory /var/www/htdocs/public/>
  Order deny,allow
  Allow from All
  Satisfy Any
</Directory>
```

## 参考
http://httpd.apache.org/docs/current/ja/mod/mod_access_compat.html#allow
