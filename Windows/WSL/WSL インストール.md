# WSL インストール

## インストール手順
### 1. 開発者モードへ変更

- スタートから設定アプリを開く。
- [更新とセキュリティ] -> [開発者向け]を開く。
- [開発者向け機能を使う]で[開発者モード]にチェックを入れる。
- ダイアログが表示されるので、[はい]を選択してダイアログを閉じる。

### 2. WSL機能のインストール

- PowerShellを管理者権限で起動する。
- 以下のコマンドを入力して、WSL機能をインストールする。インストールが終わると再起動を促されるので、再起動する。

```powershell
Get-WindowsOptionalFeature -Online -FeatureName * | ? FeatureName -like "*subsystem*"  # FeatureNmaeの確認
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux   # FeatureNameを指定して有効化
```

### 3. Bashの起動

- スタートからBashと検索して、Bashを起動する。
- Ubuntuのインストールを開始する旨のメッセージが表示されるので、yを入力して進める。
- インストールは数分かかる。
- UNIXユーザーのユーザー名とパスワード、ロケールなどの入力を促されるので入力する。
- Bashが起動する。

## インストール補足
### ビルドツールのパッケージのインストール

```powershell
sudo apt-get install build-essential

apt-get install autotools-dev
apt-get install autoconf
apt-get install libtool
apt-get install pkg-config

apt-get install ncurses-dev
```
