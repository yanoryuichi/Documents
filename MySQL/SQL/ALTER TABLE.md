# ALTER TABLE

## カラム変更

### カラム名変更

```clike
ALTER TABLE tbl1 CHANGE col1 col2 varchar(255); col1 から col2 へ
```

### カラム属性変更（NULL制約・型など）

```clike
ALTER TABLE tbl1 CHANGE col1 col1 int NOT NULL;   col1 はint型、NOT NULL制約になる

ALTER TABLE tbl1 CHANGE col1 col1 int;   すでにcol1がNOT NULLなら、これでNOT NULL制約は消える
```

## カラム追加

```clike
ALTER TABLE users ADD COLUMN age int AFTER name
```

## カラム削除

```clike
ALTER TABLE users DROP age
```

## テーブル名変更

```clike
ALTER TABLE user_tbl RENAME TO users
```

## ユニーク制約付与

```clike
ALTER TABLE users ADD unique users_login_id_uniq ( login_id );
```

## 参考
http://dev.mysql.com/doc/refman/5.7/en/alter-table.html
