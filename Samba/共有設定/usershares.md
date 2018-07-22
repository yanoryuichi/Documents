# usershares

## usershareディレクトリの作成

```clike
mkdir /var/lib/samba/usershares
chgrp users /var/lib/samba/usershares
chmod 1770 /var/lib/samba/usershares
```

- 共有の作成を許可するUNIXユーザのグループを指定する。ここではusersを指定した。


## smb.conf

```clike
[global]
  usershare path = /var/lib/samba/usershares
  usershare max shares = 100
  usershare owner only = no
```

## 共有の作成

```clike
net usershare add public /tmp/share01 "THIS-IS-SHARE01" everyone:R,user01:F
```

## 参考

- http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html
- http://www.swerdna.net.au/suseusershares.html
- http://www.atmarkit.co.jp/flinux/special/samba_n/samba_nb.html
