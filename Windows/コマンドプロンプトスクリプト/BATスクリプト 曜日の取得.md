# BATスクリプト 曜日の取得

```powershell
@echo off
setlocal
for /f %%d in ('"powershell [Int](Get-Date).DayOfWeek"') do set dow=%%d
echo %dow%
endlocal
```



## 参考
http://stackoverflow.com/questions/11364147/setting-a-windows-batch-file-variable-to-the-day-of-the-week
