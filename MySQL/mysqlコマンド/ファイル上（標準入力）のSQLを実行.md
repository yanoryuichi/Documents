# ファイル上（標準入力）のSQLを実行

## ファイル

```clike
echo "select now()" > 1.sql
mysql foo_db < 1.sql
```

## 標準入力

```clike
echo "select now()" | mysql foo_db

```

## 参考
http://dev.mysql.com/doc/refman/5.1/en/mysql-batch-commands.html
