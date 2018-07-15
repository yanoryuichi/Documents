# PowerShell Community Extensions 3のインストール

## インストール

- 以下のページからMSI形式のインストーラをダウンロードして、実行する。
- http://pscx.codeplex.com/

## 設定

- Profileファイル（C:\Users\taro\Documents\PowerShell\Microsoft.PowerShell_profile.ps1）に以下のような記述を加える。

```powershell
Import-Module Pscx -arg ~\Pscx.UserPreferences.ps1
```
