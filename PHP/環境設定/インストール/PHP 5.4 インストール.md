# PHP 5.4 インストール

## コンパイル・インストール

```bash
w3m http://jp2.php.net/get/php-5.4.0.tar.bz2/from/jp.php.net/mirror
tar jxvf php-5.4.0.tar.bz2
cd php-5.4.0/
./configure \
  --prefix=/usr/local/php \
  --disable-cgi \
  --with-zlib \
  --enable-mbstring \
  --enable-mbregex \
  --with-pgsql=/usr/local/pgsql \
  --with-pdo-pgsql \
  --with-openssl \
  --with-apxs2
make
PATH=/usr/local/apache/bin checkinstall
```

## 設定

```bash
cp php.ini-development /usr/local/php/lib/php.ini
```

php.ini:

```ini
date.timezone = Asia/Tokyo
mbstring.language = Japanese
mbstring.internal_encoding = UTF8
```

## Apaacheの設定

```clike
LoadModule php5_module modules/libphp5.so
<FilesMatch \.php$>
   SetHandler application/x-httpd-php
</FilesMatch>
```
