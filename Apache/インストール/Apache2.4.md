# Apache2.4のコンパイル・インストール

## 事前にインストールしたパッケージ

- openssl-devel
- pcre-devel
- gcc

## ソースファイルの取得

```clike
wget http://ftp.riken.jp/net/apache//httpd/httpd-2.4.1.tar.bz2
wget http://ftp.jaist.ac.jp/pub/apache//apr/apr-1.4.6.tar.bz2
wget http://ftp.jaist.ac.jp/pub/apache//apr/apr-util-1.4.1.tar.bz2
```


## アーカイブの展開

```clike
tar jxvf httpd-2.4.1.tar.bz2 
tar jxvf apr-1.4.6.tar.bz2
tar jxvf apr-util-1.4.1.tar.bz2
mv apr-1.4.6 httpd-2.4.1/srclib/apr
mv apr-util-1.4.1 httpd-2.4.1/srclib/apr-util
```

## コンパイル・インストール

```clike
cd httpd-2.4.1
./configure --prefix=/usr/local/apache --enable-so --enable-ssl=shared --enable-mpms-shared=all
make
make install
```

## ユーザ作成

```clike
groupadd apache
useradd -g apache -d /home/www apache
```

## httpd.conf

```clike
ServerRoot "/usr/local/apache"
Listen 80
KeepAlive On
KeepAliveTimeout 15
MaxKeepAliveRequests 100
Timeout 100

LoadModule unixd_module modules/mod_unixd.so
LoadModule mime_module modules/mod_mime.so
LoadModule dir_module modules/mod_dir.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule authz_core_module modules/mod_authz_core.so

<IfModule prefork.c>
    MaxClients       150
    StartServers     5
    MinSpareServers  5
    MaxSpareServers 15
</IfModule>

<IfModule worker.c>
    StartServers         2
    MaxClients         150
    MinSpareThreads     25
    MaxSpareThreads     75
    ThreadsPerChild     25
    MaxRequestsPerChild  0
</IfModule>

User apache
Group apache
ServerAdmin info@example.com
ServerName www.example.com:80
ServerTokens Full
ServerSignature Off
TypesConfig conf/mime.types
DirectoryIndex index.html
DocumentRoot "/usr/local/apache/htdocs"
LogLevel warn
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
CustomLog "|/usr/local/apache/bin/rotatelogs /usr/local/apache/logs/access_log.%Y%m%d 604800 540" combined
ErrorLog  "|/usr/local/apache/bin/rotatelogs /usr/local/apache/logs/error_log.%Y%m%d 604800 540"

<Directory />
    AllowOverride none
    Require all denied
</Directory>

<Directory "/usr/local/apache/htdocs">
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>
```

## 起動スクリプト作成（Redhat系）

```clike
cat /usr/local/apache/bin/apachectl | sed '3s/^/# chkconfig: 345 85 15\n#\n/' > /etc/rc.d/init.d/apache
chmod 755 /etc/rc.d/init.d/apache

chkconfig --list apache
chkconfig --add apache
chkconfig --list apache
```

## 起動（Redhat系）

```clike
service apache start
```
