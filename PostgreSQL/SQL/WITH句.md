# 共通表式 WITH句


## 前提

```clike
SELECT * FROM t1;
 id1 | id2
-----+-----
   1 |   2
   3 |   4
   5 |   6
(3 rows)
```

```clike
SELECT * FROM t2;
 id
----
  1
  3
(2 rows)
```

## WITHを使わない

```clike
SELECT * FROM t1 WHERE id1 IN (SELECT id FROM t2 WHERE id > 1) OR id2 IN (SELECT id FROM t2 WHERE id > 1);
```

```clike
 id1 | id2
-----+-----
   3 |   4
(2 rows)
```

## WITHを使う

```clike
WITH _t2 AS (SELECT id FROM t2 WHERE id > 1) 
SELECT * FROM t1 WHERE id1 IN (SELECT id FROM _t2) OR id2 IN (SELECT id FROM _t2);
```

```clike
 id1 | id2
-----+-----
   3 |   4
(1 row)
```

## WITHでDELETE

```clike
SELECT * FROM t1;
```

```clike
 id
-----
 100
 200
(2 rows)
```

```clike
SELECT * FROM t1_backup ;
```

```clike
 id
----
(0 rows)
```

```clike
WITH del AS (DELETE FROM t1 RETURNING id) INSERT INTO t1_backup SELECT * FROM del;
```

```clike
SELECT * FROM t1;
```

```clike
 id
----
(0 rows)
```

```clike
SELECT * FROM t1_backup ;
```

```clike
 id
-----
 100
 200
(2 rows)
```

## 参考
http://lets.postgresql.jp/documents/technical/with_recursive
