# スキーマ確認 SHOW CREATE TABLE相当

```clike
$ pg_dump -s -t TABLE_NAME
```

- SQL(psql)からはできない。
- CREATE TABLE文の他に、制約などがALTER TABLE文として出力される。

## 参考
https://serverfault.com/questions/231952/is-there-a-mysql-equivalent-of-show-create-table-in-postgres
