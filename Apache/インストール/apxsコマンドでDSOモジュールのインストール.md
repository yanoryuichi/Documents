# apxsコマンドでDSOモジュールのインストール

## Apacheのソースツリーに移動

```clike
cd /usr/local/src/apache/httpd-2.4.1/
```

## コンパイル・インストール

```clike
/usr/local/apache/bin/apxs -c modules/dav/main/mod_dav.c
sudo /usr/local/apache/bin/apxs -i -a -n dav modules/dav/main/mod_dav.la
```

- -a httpd.confにLoadModule ... を付加。
- -n dav モジュール名を明示的に指定。

## 参考

http://httpd.apache.org/docs/2.4/ja/programs/apxs.html
