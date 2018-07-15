# Elevation PowerToys

## Elevation PowerToysとは？
Elevation PowerToysは他にも機能があるが、ここでは、コンソールのPowerShellから、UACの「管理者として実行」を使って、任意のプログラムを起動する為に使う。

## ダウンロード

Elevation PowerToys 
: http://technet.microsoft.com/en-us/magazine/2007.06.utilityspotlight.aspx?pr=blog

Elevate_Win7beta_fixed.zip 
: http://blogs.technet.com/b/deploymentguys/archive/2009/01/21/the-elevation-powertoys-and-windows-7.aspx

## インストール

- Elevation PowerToysのEXEファイルを実行して、フォルダを展開する。
- Elevate_Win7beta_fixed.zipを展開して、Elevate.vbsを取り出し、上のフォルダに上書きコピーする。
- フォルダ内のElevatePowerShellScript.infを右クリックして、インストールを実行する。

## 使い方
PowerShellを起動して、以下のようにコマンドを入力する。

```powershell
 PS C:\> elevate notepad $env:windir\System32\drivers\etc\hosts
```

## 32ビット版のConsole2で使う場合
Elevate.cmdはC:\Windows\System32にインストールされるので、32ビット版のConsole2からだとリダイレクトされる。従って、以下のようにsysnativeを使ったエイリアスを設定すると良い。

```powershell
Set-Alias elevate C:\Windows\sysnative\Elevate.cmd
```
