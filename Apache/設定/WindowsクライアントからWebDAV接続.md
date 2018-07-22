# WindowsクライアントからWebDAV接続

## Windows7/8クライアントからWebDAV接続する際の挙動

- URIにドキュメントルートそのものを指定出来ないので、何かしらディレクトリを指定する。

```clike
[正しい] http://example.com/mydir
[間違い] http://example.com/
```

- AliasのURL（http://exmaple.com/myalias）では接続出来ない。

```clike
Alias /myalias /var/www/example.com/htdocs
```

- パスワードでアクセス制御する場合、ベーシック認証は使えず、ダイジェスト認証を使わなければならない。
- SSLで接続する場合、自己証明のサーバ証明書は使えない。独自CAを立てて、CA証明書をWindowsにインポートしてもダメらしい。

### 参考

- http://shon.org/blog/2010/03/04/howto-fix-windows-7-64bit-webdav/
- http://answers.microsoft.com/ja-jp/windows/forum/networking/windows8pro%E3%81%AB%E3%81%8A%E3%81%91%E3%82%8Bweb/49135a6c-5688-47b3-a376-cfadc82a8e27

## 設定

### httpd.conf グローバル設定

```clike
LoadModule dav_module modules/mod_dav.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule auth_digest_module modules/mod_auth_digest.so

DavLockDB "/usr/local/apache/var/DavLock"
```

### httpd.conf VirtualHost設定

```clike
<Directory "/var/www/example.com/htdocs">
Options FollowSymlinks Indexes
AuthType Digest
AuthName KeepOut
AuthUserFile /etc/httpd/conf/htdigest-passwd.txt
Require valid-user
Dav On
</Directory>
```

```clike
net use x: http://example.com/mydir
```

## 参考

- http://httpd.apache.org/docs/2.2/mod/mod_dav.html
- http://httpd.apache.org/docs/2.4/mod/mod_dav.html
