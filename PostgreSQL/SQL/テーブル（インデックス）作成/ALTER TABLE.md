# ALTER TABLE

## NOT NULL制約をつける

```clike
ALTER TABLE users ALTER tel SET not null;
```

## ユニーク制約をつける

```clike
ALTER TABLE member ADD CONSTRAINT login_id_passwd_key UNIQUE (login_id, passwd)
```

## 主キーの削除

```clike
ALTER TABLE users DROP CONSTRAINT users_pkey;
```

## 主キーの追加

```clike
ALTER TABLE users ADD primary key ( user_id );
```

## 型変更

```clike
ALTER TABLE users ALTER birth_day TYPE timestamp
```

birth_dayを（date型などから）timestamp型に変える。

## テーブル名変更

```clike
ALTER TABLE users RENAME TO users2;
```

## 所有者変更

```clike
ALTER TABLE users OWNER to new_owner;
```

### 参考
http://stackoverflow.com/questions/1348126/modify-owner-on-all-tables-simultaneously-in-postgresql

## 参考
http://www.postgresql.jp/document/current/html/sql-altertable.html
