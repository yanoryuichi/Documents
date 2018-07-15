# ウェブページの取得 - Invoke-WebRequest (wget)

## GET

```powershell
$res = wget http://www.yahoo.co.jp/
$res.Content | Out-File index.html
echo $res.Links.href
```

## POST

```powershell
$params = @{ name = "taro"; age = 10 } 
$res = wget -Method Post -Uri http://example.com/ -Body $params
```

## 注意点

- バイナリファイルなど容量の大きなファイルをダウンロードする用途では、Invoke-WebRequestコマンドレットは重いので、curl.exeなど別のコマンドを使った方が良い。

## 参考
http://technet.microsoft.com/library/3e3dac17-3373-4d22-a54a-9d56a4a556c3(v=wps.630).aspx
