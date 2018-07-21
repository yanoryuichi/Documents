# CREATE INDEX他

## インデックス作成

```clike
CREATE INDEX idx_id ON t1 (id);
```

```clike
ALTER TABLE t1 ADD INDEX id_idx (id);
```

- CREATE/ALTERどちらでもよい。
- インデックス名（ここではidx_id）はテーブル（ここではt1）内でユニークな名前にする。プレフィックスをidx_等に統一しておくと分かりやすい。

## インデックス削除

```clike
DROP INDEX idx_id ON t1;
```

## 参考

- http://dev.mysql.com/doc/refman/5.7/en/create-index.html
- http://dev.mysql.com/doc/refman/5.7/en/drop-index.html
