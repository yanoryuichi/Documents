# RETURNING句


### シリアル型を持つテーブルを作る

```clike
CREATE TABLE t1 ( id serial, num int );
```

### RETURNING句により今挿入したidを取得できる

```clike
INSERT INTO t1 ( num ) VALUES ( 100 ) RETURNING id;
```

```clike
 id
----
  1
```

```clike
INSERT INTO t1 ( num ) VALUES ( 200 ) RETURNING id;
```

```clike
 id
----
  2
```

```clike
SELECT * FROM t1;
```

```clike
 id | num
----+-----
  1 | 100
  2 | 200
```

### UPDATE/DELETEでも使える

```clike
DELETE FROM t1 RETURNING id;
```

```clike
 id
----
  1
  2
```

### 参考
PostgreSQL 8.2以降。
