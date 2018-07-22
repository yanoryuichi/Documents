# COPYでCSVデータをテーブルへINSERTする

### ファイルから

```clike
COPY user (name,age,tel) FROM '/tmp/user.csv' DELIMITER AS ','
```

### 標準入力から

```clike
COPY category FROM stdin DELIMITERS ',';
（↓コピペする） 
1,建設業
2,製造業
3,情報通信業
\.
```

http://www.postgresql.jp/document/pg837doc/html/sql-copy.html

### seirial型のカラムがある場合
COPYコマンドを使った後、そのテーブルにserial型のカラムがある場合、シーケンスが狂う。
例えば、プライマリキーcategory_idがserial型で、category_idを明示せずにINSERT文を実行するとエラーになる。

```clike
INSERT INTO category (category_name) values ( 'サービス業');
ERROR:  duplicate key violates unique constraint "category_pkey"
```

この場合、下のようにシーケンスを操作する。

```clike
SELECT setval('category_category_id_seq',(SELECT max(category_id) FROM category))
```

http://www.postgresql.jp/document/pg837doc/html/functions-sequence.html
