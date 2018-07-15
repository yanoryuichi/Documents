# ショートカット(lnk)の作成

```powershell
$WshShell = New-Object -ComObject WScript.Shell
$ShortCut = $WshShell.CreateShortcut("C:\tmp\mycalc.lnk")
$ShortCut.TargetPath = "calc.exe"
$ShortCut.Save()
```

- ショートカットとシムリンクは別のものなので注意。
- CreateShortcut()の引数は絶対パスが必要なようだ。

## 参考
http://www.computerperformance.co.uk/powershell/powershell_create_shortcut.htm
