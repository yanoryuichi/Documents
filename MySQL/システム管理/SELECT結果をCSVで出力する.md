# SELECT結果をCSVで出力する

## シェルからSQLを実行してファイルへリダイレクトする
ヘッダを除外してカンマ区切りで出力する

```clike
mysql -h db_server -B -e 'SELECT * FROM t1' my_db | tail +2 | sed -e 's/\t/,/g'
```

```clike
mysql my_db < ./test.sql > output.csv
```

## SELECT INTO

```clike
ssh db_server "mysql -B -e \"SELECT * FROM t1 into outfile '/tmp/dump.sql' FIELDS TERMINATED BY ',' \" my_db;
scp db_server:/tmp/dump.sql .
```

http://yanor.net/wiki/?MySQL%2F%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E7%AE%A1%E7%90%86%2FSELECT%E7%B5%90%E6%9E%9C%E3%82%92CSV%E3%81%A7%E5%87%BA%E5%8A%9B%E3%81%99%E3%82%8B
