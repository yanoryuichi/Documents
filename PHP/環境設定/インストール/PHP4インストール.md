# PHP4インストール

```clike
./configure \
--with-apxs2=$HOME/apache/bin/apxs \
--enable-mbstring \
--enable-mbregex \
--enable-zend-multibyte \
--with-mysql \
--enable-track-vars \
--enable-trans-sid \
--enable-pgsql
```

```clike
AddType application/x-httpd-php .php
```
