# mountvol - ディスクのマウント

## ボリューム一覧

```powershell
mountvol /l
```

もしくは

```powershell
echo list volume | diskpart
```

## マウント

```powershell
mountvol F:\ \\?\Volume{7f1a0b73-a297-11d3-9849-806d6172696f}\
```

「7f1a0b73-a297-11d3-9849-806d6172696f」はディスクのGUID。mountvol /lで確認出来る。

## アンマウント

```powershell
mountvol F: /d
```

ここではFドライブをアンマウントした。


## 参考

- http://technet.microsoft.com/ja-jp/library/cc772671(v=ws.10).aspx
