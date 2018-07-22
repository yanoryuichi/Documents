# Apache1.3 + mod_sslインストール

mod_sslのアーカイブに含まれるINSTALLファイルが詳しい。

## OpenSSLの準備
mod_sslのコンパイルに使うだけでインストールはしない。

```clike
cd /usr/local/src
wget http://www.openssl.org/source/openssl-0.9.8e.tar.gz
tar zxvf openssl-0.9.8e.tar.gz 
cd openssl-0.9.8e/
sh config no-idea no-threads -fPIC
make
make test
```

## Apacheの準備

```clike
cd ..
wget http://ftp.kddilabs.jp/infosystems/apache/httpd/apache_1.3.37.tar.gz
tar zxvf apache_1.3.37.tar.gz
```

## mod_sslの準備
Apacheのコンパイルオプションをここで指定する。

```clike
cd ..
wget http://www.modssl.org/source/mod_ssl-2.8.28-1.3.37.tar.gz
tar zxvf mod_ssl-2.8.28-1.3.37.tar.gz 
cd mod_ssl-2.8.28-1.3.37/
./configure --with-apache=../apache_1.3.37 --with-ssl=../openssl-0.9.8e 
--prefix=/usr/local/apache13 --enable-module=so --enable-shared=max
--enable-module=rewrite --enable-shared=rewrite
--enable-module=ssl --enable-shared=ssl

```

## Apacheのコンパイルとインストール

```clike
cd ../apache_1.3.37/
make
make certificate TYPE=dummy
make install
```
