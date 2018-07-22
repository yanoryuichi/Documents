# SELECT結果でUPDATE

## 前提

```clike
テーブル T1
 id | num 
----+-----
  1 | 100
  2 | 200
  3 | 300
```

```clike
テーブル T2
 id | num 
----+-----
  1 |   1
  3 |   3
```

## 求めたい結果

```clike
テーブルT1
 id | num 
----+-----
  1 | 1
  2 | 200
  3 | 3
```

## SQL

```clike
UPDATE t1 SET num = a.num FROM (SELECT * FROM t2) a WHERE t1.id = a.id;
```

## 注意
以下のような相関サブクエリを使ったUPDATEではid 2の行のnumがヌルになってしまう。

```clike
UPDATE t1 SET num = ( SELECT num FROM t2 WHERE t2.id = t1.id );
```

```clike
テーブルT1
  id | num 
----+-----
  1 |   1
  2 |    
  3 |   3
```
