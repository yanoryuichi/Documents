# NOT INのサブクエリにNULLが含まれる場合の回避方法

## 前提

```clike
# SELECT * FROM t1;
 t1_id | t2_id
-------+-------
     1 |   100
     2 |   100
     3 |   200
     4 |   300
(4 行)
```

```clike
# SELECT * FROM t2;
 t2_id
-------
   100
   200
   400

(4 行)
```

t2にNULLなレコードがある。

## NOT IN

```clike
# SELECT * FROM t1 WHERE t2_id NOT IN ( SELECT t2_id FROM t2 );
 t1_id | t2_id
-------+-------
(0 行)
```

NULLが他の値（300）より優先されるため、期待した結果にならない。

## 回避方法：NOT EXISTS

```clike
# SELECT * FROM t1 WHERE NOT EXISTS ( SELECT t2.t2_id FROM t2 WHERE t1.t2_id = t2.t2_id  );
 t1_id | t2_id
-------+-------
     4 |   300
(1 行)
```
