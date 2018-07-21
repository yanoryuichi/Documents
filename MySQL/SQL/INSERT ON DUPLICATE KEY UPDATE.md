# INSERT ON DUPLICATE KEY UPDATE

## 準備

```clike
CREATE TABLE `t1` (
 `id1` int(11) DEFAULT NULL,
 `id2` int(11) DEFAULT NULL,
 `id3` int(11) DEFAULT NULL,
 UNIQUE KEY `t1_unique_id1_id2` (`id1`,`id2`)
);
INSERT INTO `t1` VALUES (1,2,100),(2,3,200),(1,3,300);
```

## 使い方
### テーブル確認

```clike
SELECT * FROM t1;
+------+------+------+
| id1  | id2  | id3  |
+------+------+------+
|    1 |    2 |  100 |
|    2 |    3 |  200 |
|    1 |    3 |  300 |
+------+------+------+
```

### ユニーク制約違反のINSERT
上の状態で下のようにINSERTするとユニーク制約でエラーになる。

```clike
INSERT INTO t1 (id1, id2, id3) VALUES (1, 2, 500);
```

### INSERT ON DUPLICATE KEY UPDATE
そこで下のようにINSERT ON DUPLICATE KEY UPDATEすると、

```clike
INSERT INTO t1 (id1, id2, id3) VALUES (1, 2, 500) ON DUPLICATE KEY UPDATE id3 = 600;
```

下のようにid3が600でUPDATEされる。

```clike
SELECT * FROM t1;
+------+------+------+
| id1  | id2  | id3  |
+------+------+------+
|    1 |    2 |  600 |
|    2 |    3 |  200 |
|    1 |    3 |  300 |
+------+------+------+
```

### ユニーク制約じゃないINSERT
下のようにユニーク制約に関係ないINSERTは、

```clike
INSERT INTO t1 (id1, id2, id3) VALUES (4, 4, 700) ON DUPLICATE KEY UPDATE id3 = 800;
```

そのままINSERTされる。

```clike
SELECT * FROM t1;
+------+------+------+
| id1  | id2  | id3  |
+------+------+------+
|    1 |    2 |  600 |
|    2 |    3 |  200 |
|    1 |    3 |  300 |
|    4 |    4 |  700 |
+------+------+------+
```

## 参考
http://dev.mysql.com/doc/refman/5.1/ja/insert-on-duplicate.html
