# HTTP TRACEの禁止
httpd.confに

```clike
RewriteEngine On                  
RewriteCond %{REQUEST_METHOD} ^TRACE
RewriteRule .* - [F]
```

詳しくは、http://www.atmarkit.co.jp/fsecurity/rensai/webhole04/webhole01.html
