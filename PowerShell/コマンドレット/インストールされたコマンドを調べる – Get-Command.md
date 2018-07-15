# インストールされたコマンドを調べる - Get-Command

## 全コマンド一覧を取得

```powershell
Get-Command
```

## ワイルドカードでコマンドを探す

```powershell
Get-Command *diff*
```

```powershell
PS taro> Get-Command *diff*

CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           diff -> Compare-Object
Application     diff.exe
Application     docdiff.exe
Application     kdiff3.exe
Application     TortoiseIDiff.exe
Application     TortoiseUDiff.exe
```

## （コマンドではなく）インストールされたプログラムの一覧を取得

```powershell
Get-WmiObject win32_product | select name
Get-WmiObject win32_product | ? { $_.name -like "*office* } | ft -a
```

## 参考
http://technet.microsoft.com/ja-JP/library/hh849711.aspx
