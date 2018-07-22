# 任意のHTTPヘッダを消す

mod_headersを使う。Apacheの設定からなるHTTPヘッダや、mod_php内のPHPプログラムで指定したHTTPヘッダを消す事が出来る。
Perl/CGI等で、CGIの中でprint "x-test: 123";のようにHTTPヘッダ出力すると消す事が出来ないようだ。

```clike
<Directory /foo/var>
Header unset Pragma
Header unset Expires
Header unset x-test
</Directory>
```

## 参考
http://httpd.apache.org/docs/2.2/ja/mod/mod_headers.html
