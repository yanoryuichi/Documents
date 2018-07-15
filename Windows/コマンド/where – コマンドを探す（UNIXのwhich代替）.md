# where - コマンドを探す（UNIXのwhich代替）

## 使い方

```powershell
>where notepad
C:\Windows\System32\notepad.exe
C:\Windows\notepad.exe
```

※ whereはWindows Server 2003及びVista以降で標準インストールされている。

## UNIXのwhich代替として使う場合

```powershell
>where notepad123
情報: 与えられたパターンのファイルが見つかりませんでした。
```

コマンドが見つからない場合はエラー出力にメッセージが表示されるので、以下のようにリダイレクトするか、

```powershell
>where notepad123 2>nul
```

以下のように/Qで出力を抑制してリターンコードを利用する。なお、下はBATスクリプトの場合。

```powershell
where /Q notepad123
if not %ERRORLEVEL% == "0" echo "Not Found" 
```

## PowerShellの場合
Get-Commandコマンドレットを使う。

```powershell
Get-Command notepad
```
