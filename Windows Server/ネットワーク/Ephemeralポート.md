# Ephemeralポート

## ポート範囲

| Windows Vista/Windows Server 2008以降 | 49152 - 65535 |
| Widows XP/Windows Server 2003以前 | 5000 - 65534 |

## netshコマンド

```clike
netsh int ipv4 show dynamicport tcp
```

## 参考

- http://support.microsoft.com/kb/929851
- http://akihatoetsu.tumblr.com/post/77564420109/aws-vpc-ephemeral-port
