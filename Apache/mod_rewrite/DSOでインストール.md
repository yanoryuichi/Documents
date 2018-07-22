# mod_rewriteをDSOでインストール

1. DSOが使用可能か確認する。


```clike
cd /usr/local/apache/bin
./httpd -l | grep mod_so
```

1. Apacheのバージョンを確認する。


```clike
./httpd -v
```

1. そのバージョンのApacheをダウンロードする。


```clike
wget http://archive.apache.org/dist/httpd/xxx.tar.gz
```

1. 解凍してmod_rewriteのソースファイルを探す。


```clike
cd /usr/local/src/apache
find . -name 'mod_rewrite*'
```

1. コンパイルしてインストールする。


```clike
/usr/local/apache/bin/apxs -I/usr/include/gdbm -c mod_rewrite.c
/usr/local/apache/bin/apxs -i mod_rewrite.so
```

1. httpd.confを編集してApacheの設定を修正する。


```clike
LoadFile /usr/lib/libgdbm.so
LoadModule rewrite_module modules/mod_rewrite.so
```

1. Apacheを再起動する。


```clike
/usr/local/apache/bin/apachectl restart
```

## 参考
http://httpd.apache.org/docs/2.0/ja/programs/apxs.html
