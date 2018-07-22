# TCP接続を解放する

### postgresql.conf

```clike
listen_addresses = 'localhost,192.168.0.100' 
```

### pg_hba.conf

```clike
host  all  taro 192.168.0.0/24  trust
```

## 参考

- http://www.postgresql.jp/document/9.1/html/runtime-config-connection.html#RUNTIME-CONFIG-CONNECTION-SETTINGS
- http://www.postgresql.jp/document/9.1/html/auth-methods.html#AUTH-TRUST
- http://www.postgresql.org/docs/9.1/static/auth-pg-hba-conf.html
