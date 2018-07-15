# コマンド履歴 Get-History他

### 直近N回

```powershell
history -Count 3
```

### ユニーク

```powershell
history | select -Unique
```

### 検索

```powershell
history | ? CommandLine -like "cd"

```

## 参考
https://technet.microsoft.com/en-us/library/ee176849.aspx
