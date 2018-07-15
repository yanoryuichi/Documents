# PowerShellスクリプトをタスクスケジューラに登録

## タスクスケジューラに登録する際の注意点

- "プログラム"に直接PSスクリプトを指定せず、以下のようにpowershell.exeに引数として渡すように指定する。
- [プログラム] %SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe
- [引数の追加] -Command C:\bat\test.ps1
- [開始] （PS1スクリプト実行時のワーキングディレクトリ）

### 参考
http://www.atmarkit.co.jp/ait/articles/1412/03/news125.html

## リターンコード

- 正常終了する場合はexit 0を記述する。
- 異常終了する場合はexit 1（0以外）を記述する。


## イベントログ

- Microsoft->Windows->TaskScheduler

```powershell
PS> Get-WinEvent Microsoft-Windows-TaskScheduler/Operational -MaxEvents 3
```

## ウィンドウを隠す

```powershell
PowerShell.exe -windowstyle hidden { your script.. }
```

### 参考
http://stackoverflow.com/questions/1802127/how-to-run-a-powershell-script-without-displaying-a-window
