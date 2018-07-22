# データが初出の場合だけINSERTする

t1テーブルのidカラムにまだ100がない場合だけ100をINSERTする。次回このSQLを実行してもすでに100があるのでINSERTされない。

```clike
INSERT INTO t1 (id) SELECT 100 WHERE (SELECT COUNT(*) FROM t1 WHERE id = 100) = 0;
```
