# BTree以外のインデックス

```clike
CREATE INDEX members_email_idx USING hash ON members (email);
```

## 参考
http://www.postgresql.jp/document/current/html/indexes-types.html
