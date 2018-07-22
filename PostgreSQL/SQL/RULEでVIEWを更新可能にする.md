# RULEでVIEWを更新可能にする

## テーブルとそのビューを作る

```clike
CREATE TABLE t1 ( id int );
CREATE VIEW v1 AS SELECT id FROM t1;
```


## ビューにルールを作る

```clike
CREATE RULE rule_1 AS ON INSERT TO v1 DO INSTEAD INSERT INTO t1 ( id ) VALUES ( NEW.id );
```

## ビューにインサートする

```clike
INSERT INTO v1 ( id ) VALUES ( 100 );
```
