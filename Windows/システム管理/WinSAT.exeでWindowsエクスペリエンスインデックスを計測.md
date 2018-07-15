# WinSAT.exeでWindowsエクスペリエンスインデックスを計測

### cmd.exe

```powershell
winsat formal -restart clean
```

ファイルに出力される。

### powershell

```powershell
Get-WmiObject -Class Win32_WinSAT
```

インデックスだけ表示される。

## 参考
http://www.atmarkit.co.jp/ait/articles/1403/14/news052.html
