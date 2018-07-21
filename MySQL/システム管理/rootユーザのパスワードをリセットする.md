# rootユーザのパスワードをリセットする

## 手順

- mysqldを停止する。
- mysqldを以下のようにオプション指定して起動する。（すると、パスワード無しでMySQLにログイン出来る。）

```clike
shell> mysqld_safe --skip-grant-tables 
```

- パスワードを設定する。

```clike
UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;
```

- mysqldを停止する。
- mysqldを通常起動する。

## 参考
http://dev.mysql.com/doc/refman/5.6/en/resetting-permissions.html
