# touch

## ファイルを作成

```powershell
New-Item -Type file foo.txt
ni -type file foo.txt
```

## 日付を変更

```powershell
dir | % { $_.LastWriteTime = "2014-01-01 00:00:00" }
```
