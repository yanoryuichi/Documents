#MySQL Tips
## REPLACE
INSERTと同機能だが、すでに同じ主キーのレコードがある場合、UPDATEとして機能する。主キーがないテーブルには意味ない。MySQLオリジナルなSQL。

```clike
REPLACE INTO tbl VALUES ( 100, 'test' );
```
