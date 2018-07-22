# UNIXクライアントからマウントする

## クライアントPCからSambaサーバ上のフォルダをマウントする

```clike
sudo mount_smbfs //taro@192.168.0.100/myshare01 /mnt/myshare01
```

- taro: 認証に使うユーザ名
- 192.168.0.100: Sambaサーバ
- myshare01: Samba共有名（リモートのマウント元）
- /mnt/myshare01: ローカルのマウント先

## 起動時にマウントする

/etc/fstab :

```clike
//taro@192.168.0.100/myshare01 /mnt/myshare01 smbfs rw,-I=192.168.0.100 0 0
```

/etc/nsmb.conf :

```clike
[192.168.0.100:TARO]
password=taropasswd
```
