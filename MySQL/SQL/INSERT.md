# INSERT

## SELECT結果でINSERT

```clike
INSERT INTO users (user_id, password, status) SELECT user_id, login_id, password, 1 FROM users2;
```
