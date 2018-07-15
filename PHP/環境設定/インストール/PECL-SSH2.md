# PECL-SSH2

- PHP 5.2
- OpenSSL 1.0.0d
- libss2 1.2.9
- PECL::SSH2 0.11.2

```bash
mkdir -p p/home/taro/php/src/{openssl,libssh2,php,pecl-ssh2}

cd /home/taro/php/src/openssl/
wget http://www.openssl.org/source/openssl-1.0.0d.tar.gz
tar zxvf openssl-1.0.0d.tar.gz
cd openssl-1.0.0d/
./config --prefix=/home/taro/php shared
make
make install

cd /home/taro/php/src/libssh2/
wget http://www.libssh2.org/download/libssh2-1.2.9.tar.gz
tar zxvf libssh2-1.2.9.tar.gz
cd libssh2-1.2.9/
./configure --help
./configure --prefix=/home/taro/php --with-libssl-prefix=/home/taro/php
make
make install

cd /home/taro/php/src/php/
cp /home/taro/tmp/php-5.2.17.tar.bz2 .
tar jxvf php-5.2.17.tar.bz2
cd php-5.2.17/
./configure --prefix=/home/taro/php/
make
make install
cp php.ini-dist /home/taro/php/lib/php.ini

cd /home/taro/php/src/pecl-ssh2/
wget http://pecl.php.net/get/ssh2-0.11.2.tgz
tar zxvf ssh2-0.11.2.tgz
cd ssh2-0.11.2
~/php/bin/phpize
./configure --with-php-config=/home/taro/php/bin/php-config --with-ssh2=/home/taro/php/
make
make install

vi /home/taro/php/lib/php.ini:
> extension=ssh2.so
> extension_dir = "/home/taro/php/lib/php/extensions/no-debug-non-zts-20060613"

/home/taro/php/bin/php -m | grep ssh
> ssh2
```
