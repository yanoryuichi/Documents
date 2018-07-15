# コマンドや関数の概要を取得する Get-Command

## 指定したパラメータを持つコマンドレットを調べる

```powershell
PS tmp> Get-Command -ParameterName recurse

CommandType Name          Version Source
----------- ----          ------- ------
Cmdlet      Copy-Item     3.1.0.0 Microsoft.PowerShell.Managemen
Cmdlet      Get-ChildItem 3.1.0.0 Microsoft.PowerShell.Managemen
（略）
```

## 実行可能か調べる（パスが通っているか調べる）

```powershell
if ((Get-Command "no-such-app.exe" -ErrorAction SilentlyContinue) -eq $Null) {
  echo "The app is not found"
}
```

## 参考
http://ss64.com/ps/get-command.html
