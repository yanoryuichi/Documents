# PHP5.3インストール

## CLI版

```clike
./configure --prefix=$HOME/opt/php53 \
--disable-cgi \
--with-zlib \
--enable-mbstring \
--enable-mbregex \
--with-mysql=/usr/local/mysql \
--with-pdo-mysql
```
