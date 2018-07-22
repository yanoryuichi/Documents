# SELECT結果でINSERT

## 実行前
### t1テーブル

```clike
 id
----
  2
  3
(2 rows)
```

### t2テーブル

```clike
 id | num
----+-----
(0 rows)
```

## 実行

```clike
 INSERT INTO t2 ( id, num ) SELECT id, 999 FROM t1;
```

## 実行後

```clike
 id | num
----+-----
  2 | 999
  3 | 999
(2 rows)
```
