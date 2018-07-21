# INSERT実行後に行数を取得

```clike
echo "INSERT INTO t1 VALUES ( 1 )" | mysql -vvv foo_db
```

もしくは SELECT ROW_COUNT() を実行する。


## 参考
http://stackoverflow.com/questions/25397635/mysql-commandline-execution-of-query-with-its-output-having-the-rows-affected
