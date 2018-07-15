# VBScript

## 外部プログラムの実行

```powershell
arg = "%USERPROFILE%\Documents\tmp\test.txt"
CreateObject("WScript.Shell").Run "notepad.exe " & arg, 0, False
```
