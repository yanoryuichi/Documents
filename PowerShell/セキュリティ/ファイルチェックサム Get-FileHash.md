# ファイルチェックサム Get-FileHash

```powershell
Get-FileHash -Algorithm MD5 "C:\foo.exe"
```

### PowerShell ver4より前の場合

```powershell
$path = "C:\foo.txt"
$md5 = New-Object -TypeName System.Security.Cryptography.MD5CryptoServiceProvider
$hash = [System.BitConverter]::ToString($md5.ComputeHash([System.IO.File]::ReadAllBytes($path)))
```

## 参考

- http://stackoverflow.com/questions/10521061/how-to-get-an-md5-checksum-in-powershell
