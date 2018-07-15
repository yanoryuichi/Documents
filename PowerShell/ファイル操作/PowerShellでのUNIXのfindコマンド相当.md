# PowerShellでのUNIXのfindコマンド相当

## findコマンド

```powershell
Get-ChildItem -Recurse -Filter '*.exe'
```

```powershell
Get-ChildItem $env:USERPROFILE\tmp -Include *.txt,*.jpg -Exclude *.bak.txt -Recurse
```

## find -execute コマンド相当

```powershell
Get-ChildItem $env:USERPROFILE\tmp -Include *.txt,*.jpg -Exclude *.bak.txt -Recurse | Remove-Item -WhatIf
WhatIf: 対象 "C:\Users\nigeria\tmp\dir1\2.txt" に対して操作 "ファイルの削除" を実行しています。
WhatIf: 対象 "C:\Users\nigeria\tmp\1.txt" に対して操作 "ファイルの削除" を実行しています。
```
