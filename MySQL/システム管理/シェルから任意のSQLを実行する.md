#シェルから任意のSQLを実行する

## 基本

```clike
mysql -e 'SELECT * FROM users' foo_db
```

## --batch, -B
カラムのセパレーター（罫線）を省く。

```clike
$ mysql foo_db "select * from t1" > foo_db.csv
id1     id2     id3
1       2       600
2       3       200
```

```clike
$ mysql foo_db -e "select * from t1";
+------+------+------+
| id1  | id2  | id3  |
+------+------+------+
|    1 |    2 |  600 |
|    2 |    3 |  200 |
+------+------+------+
```

### タブ区切りでなくカンマ区切りにする

```clike
$ mysql foo_db "select * from t1" | sed -e 's/\t/,/g' > foo_db.csv
```

sedのような外部コマンドを使うしかない。

## --skip-column-names, -N
カラム名を省く。

```clike
$mysql foo_db -N -e "select * from t1";
+------+------+------+
|    1 |    2 |  600 |
|    2 |    3 |  200 |
+------+------+------+
```

## 参考
http://dev.mysql.com/doc/refman/5.1/en/mysql-command-options.html
