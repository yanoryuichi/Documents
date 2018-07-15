# GIT_SSHを使ってssh_configを指定する

## 目的と方針

- msysgitはSSH接続時に$HOME/.ssh/configを参照するが、別のファイルを参照させたい。
- そこで、別のファイルを参照するsshコマンドのラッパーを作成して、環境変数GIT_SSHで指定する。

## 手順
### 1. git-ssh.bat作成

```bash
@echo off
"C:\Program Files (x86)\Git\bin\ssh.exe" -F %APPDATA%\SSH\config %*
```

上のファイルを適当な場所に設置する。

### 2. 環境変数GIT_SSH設定

```bash
setx GIT_SSH C:\App\bin\git-ssh.bat
```

## 補足

- .ssh/configを利用するには、Windows環境変数%HOME%を指定する。
- システムワイドのssh_configは <installPath>\Git\etc\ssh\ssh_config にある。
- http://stackoverflow.com/questions/9513712/git-ssh-client-for-windows-and-wrong-path-for-ssh-config-file
