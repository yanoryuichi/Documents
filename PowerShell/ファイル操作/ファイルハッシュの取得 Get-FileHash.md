# ファイルハッシュの取得 Get-FileHash

```powershell
dir C:\tmp\*.txt | Get-FileHash

Algorithm       Hash                Path
---------       ----                ----
SHA256          ABC1234576890       C:\tmp\1.txt
SHA256          XYZ0987654321       C:\tmp\2.txt
```

### アルゴリズム指定

```powershell
dir * | Get-FileHash -Algorism MD5
```

### CSVで管理

```powershell
dir C:\tmp\*.txt | Get-FileHash | Export-Csv files.csv
Import-Csv files.csv
```

## 参考
https://technet.microsoft.com/en-us/library/dn520872.aspx
