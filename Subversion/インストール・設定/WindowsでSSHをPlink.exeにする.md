# WindowsでSSHをPlink.exeにする

- %APPDATA%\Subversion\config を開き、以下のようにtunnelsの項にsshを指定する。

```bash
[tunnels]
ssh = C:/Program Files/TortoiseSVN/bin/TortoisePlink.exe
```

### ログを取る場合

```bash
ssh = C:/Program Files/TortoiseSVN/bin/TortoisePlink.exe -v -sshlog "C:/temp/ssh.log"
```
