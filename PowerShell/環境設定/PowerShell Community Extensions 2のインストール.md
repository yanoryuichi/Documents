# PowerShell Community Extensions 2のインストール


## 手順

### Pscxのダウンロードと設置

- http://pscx.codeplex.com/からPscx-2.0.0.1.zipダウンロードする。
- Pscx-2.0.0.1.zipを右クリックして、ブロック解除ボタンをクリックする。
- マイドキュメント以下に下のようなフォルダを作る。

```powershell
C:\Users\taro\Documents\WindowsPowerShell\Modules
```

- Pscx-2.0.0.1.zipを展開して出来たPscxフォルダを上のフォルダの中にコピーする。

### スクリプトの実行ポリシーを変更する

```powershell
Set-ExecutionPolicy RemoteSigned
Get-ExecutionPolicy
```

### PowerShell設定ファイルを変更する
C:\Users\taro\Documents\WindowsPowerShellにMicrosoft.PowerShell_profile.ps1というファイルを作り、以下のように記述する。

```powershell
import-module pscx
```

ユーザ設定ファイルを利用する場合は以下のようにする。

```powershell
import-module Pscx -arg $(Join-Path -Path $profile -ChildPath "..\Pscx.UserPreferences.ps1")  
```

## スクリプトの実行ポリシーを変更せずに自分で署名する場合
### 事前準備
Makecert.exeが必要なので、Visual Studioをインストールする。

### 鍵の作成

- スタートメニューから[Visual Studio]→[Visual Studio tools]→[Visual Studio コマンドプロンプト]を選び、右クリックして管理者として実行する。
- 以下のようにして鍵を作成する。 

```powershell
cd %USERPROFILE%
makecert -n "CN=PowerShell Local Certificate Root" `
  -a sha1 -eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer -ss Root - sr localMachine
makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
  -eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

### スクリプトの署名

- PowerShellを管理者として実行する。
- 署名する為のツールスクリプトを作成する。パスの通った場所に以下のようなスクリプトファイルadd-sinature.ps1を作成する。

```powershell
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

- 以下のようにしてadd-sinature.ps1を署名する。

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

### 参考

- get-help about_signing
- http://www.atmarkit.co.jp/fwin2k/win2ktips/1023ps1sec/ps1sec.html
