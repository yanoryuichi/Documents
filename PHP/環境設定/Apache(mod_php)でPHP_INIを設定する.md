# Apache(mod_php)でPHP_INIを設定する


## .htaccess または httpd.conf

```clike
php_flag log_errors On
php_value error_log "/tmp/php_error.log"
```


## 参考

- http://stackoverflow.com/questions/22858889/use-php-flag-in-htaccess
- http://stackoverflow.com/questions/33320057/how-to-log-an-php-error-log-error-message-to-apache-server-error-log/33320149#33320149
