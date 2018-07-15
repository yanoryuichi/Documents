# set - setx - 環境変数の操作

## set

### 代入・再代入

```powershell
set mesg=hello
echo %mesg%
  => "hello"

set mesg=%mesg%, world
echo %mesg%
  => "hello, world"
```

### 数値演算

```powershell
set num1=10
set /a num2=%num1%*2
echo %num2%
  => "20"
```

### 文字列置換

```powershell
set mesg=foo
set mesg=%mesg:oo=xx%
echo %mesg%
  => "fxx"
```

### 部分文字列の取り出し

```powershell
set mesg=foo
set mesg=%mesg:~0,2%
echo %mesg%
  => "fo"
```

### 参考
http://www.geocities.co.jp/SiliconValley-SanJose/1227/variable.html

## setx
### ユーザ環境変数の設定

```powershell
setx PATH "%PATH%;C:\App\bin"
```

### システム環境変数の設定

```powershell
setx /m PATH "%PATH%;C:\App\bin"
```

### 環境変数のクリア

```powershell
setx FOO ""
```

環境変数FOOの値が""になるが、FOOキーは残る。

### 環境変数の削除

```powershell
reg delete HKCU\Environment /v FOO
```

レジストリからエントリーを削除することによって、環境変数FOOそのものが削除される。

### 参考

- http://www.atmarkit.co.jp/fwin2k/win2ktips/1003setx/setx.html
- http://www.atmarkit.co.jp/fwin2k/win2ktips/1006setxf/setxf.html
- http://stackoverflow.com/questions/13222724/command-line-to-remove-an-environment-variable-from-the-os-level-configuration
