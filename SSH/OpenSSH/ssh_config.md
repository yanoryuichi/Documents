# ssh_config

## Hostのワイルドカードによる指定

```
Host x.example.com
User foo
IdentityFile ~/.ssh/id_rsa_for_host_x

Host *
User bar
IdentityFile ~/.ssh/id_rsa
```

Hostのワイルドカードは最初にマッチする項目が採用されるので、グローバルな設定はconfigの最後に書く。

### 参考
http://unix.stackexchange.com/questions/16571/multiple-host-in-ssh-config
