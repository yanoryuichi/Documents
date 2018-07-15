# Pagerをlessにする

## PSCXをインストール

- PSCX(PowerShell Community Extension)をインストールする。

## Pagerの変更の有効化・無効化
C:\Users\taro\Documents\WindowsPowerShell以下のPscx.UserPreferences.ps1にて以下のように$trueもしくは$falseに設定をする。

```powershell
@{
  PageHelpUsingLess = $true
}
```

## lessの設定
C:\Users\taro\Documents\WindowsPowerShell以下のMicrosoft.PowerShell_profile.ps1にて以下のように設定をする。詳しくはUNIX系のlessのドキュメントを参照の事。

```powershell
$Env:LESSHISTFILE = $Env:AppData + "\PowerShell\_lesshst"
$Env:LESS="-q"

Import-Module Pscx -arg ~\Documents\WindowsPowerShell\Pscx.UserPreferences.ps1 
```

### man of less
http://linuxjm.sourceforge.jp/html/GNU_less/man1/less.1.html

## lessの設置場所

```powershell
C:\Program Files (x86)\PowerShell Community Extensions\Pscx3\Pscx\Apps\less.exe
```

## 参考
http://www.lincolnblog.net/PowerShell-Community-Extensions-PSCX.ashx
