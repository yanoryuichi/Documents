# 自己署名のSSLサイト

## 自己署名でサーバ鍵を作る

```clike
openssl genrsa -rand /var/log/maillog -out server.key 1024
openssl req -new -x509 -days 3650 -key server.key > server.crt
```

### 参考
[[セキュリティ・PKI/OpenSSLを使った鍵・証明書の作成]]

## Apacheの設定（ネームバーチャルホストの場合）

```clike
Listen 443
NameVirtualHost *:443
<VirtualHost *:443>
   ServerName www.example.com
   DocumentRoot /home/www/htdocs
   ErrorLog /home/www/logs/error_log
   CustomLog /home/www/logs/access_log common
   <ifModule mod_ssl.c>
       SSLEngine on
       SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
       SSLCertificateFile /usr/local/etc/apache22/server.crt
       SSLCertificateKeyFile /usr/local/etc/apache22/server.key
   </ifModule>
   <Directory />
       Order Deny,Allow
       Allow from All
       Options All
       AllowOverride All
   </Directory>
</VirtualHost>
```
