# my.cnfファイルにパスワードを保存する

### $HOME/.my.cnf

```clike
[client]
user=taro
password="taro_no_password"
```

```clike
chmod 600 $HOME/.my.cnf
```

注意） パスワードの指定には引用符（""）が必要

## 参考
http://dev.mysql.com/doc/refman/5.1/ja/password-security.html
