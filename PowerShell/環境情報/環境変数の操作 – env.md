# 環境変数の操作 - env

## 環境変数一覧を取得する

```powershell
Get-ChildItem env:
dir env:             # エイリアス
```

## 環境変数を検索する

```powershell
Get-ChildItem -Path env:*user*
```


## 環境変数を取得する

```powershell
Get-ChildItem env:APPDATA
```

## 環境変数を修正する

```powershell
$env:Path += ";C:\foo\bin"
```

## 永続的に環境変数を修正する

```powershell
[Environment]::SetEnvironmentVariable( "foo", 123, [System.EnvironmentVariableTarget]::Machine )
```

```powershell
[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\bin", [EnvironmentVariableTarget]::Machine
```

### コマンドプロンプトを使う場合

```powershell
setx Path "c:\java\bin"
```

## 参考

- https://stackoverflow.com/questions/714877/setting-windows-powershell-path-variable
- https://ss64.com/ps/syntax-env.html
