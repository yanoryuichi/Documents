# CSVでインポート・エクスポート


## CSVを読み取る

```clike
COPY user_table ( user_id, name, age) from '/tmp/user.csv' WITH CSV;
```

## CSVで表示（デリミタの変更）

```clike
\pset tuples_only 
\pset pager off
\pset format unaligned
\pset fieldsep ','
```

## 結果をファイルに書き出す

```clike
\o '/tmp/result'
select * from users;
\o   （で元に戻す）
```

## （シェルから）検索結果をCSVに出力する

```clike
echo "select * from users" | psql -A -F ',' -t -U postgres some_db > users.csv

-A 位置揃え無しの出力モード
-F 'sep' フィールド区切り文字の指定
-t ヘッダフッタを抑制する
```

## COPY （SQLコマンド）

```clike
COPY (SELECT * FROM users LIMIT 3) TO '/tmp/users.csv' 
  (FORMAT 'csv', QUOTE '"', FORCE_QUOTE *, NULL " ", HEADER 1);
```

- super userで実行する必要がある。
- ファイルはPostgreSQLサーバ上に作成される。

### 参考
http://www.postgresql.jp/document/9.6/html/sql-copy.html

## \copy (psqlコマンド)

```clike
\copy ( SELECT * FROM users ) TO '/tmp/users.csv' with DELIMITER ',' NULL '' CSV HEADER
```

- super userでなくても実行できる。
- ファイルはpsqlコマンドを実行したホスト上に作成される。
- \copyコマンドは1行で入力する。改行してはいけない。

### 参考
http://www.postgresql.jp/document/9.6/html/app-psql.html#app-psql-meta-commands-copy
