# PuTTYの環境変数をサーバへ渡す (Environment variables)

## PuTTYの設定

- 設定ダイアログを開く。
- "Connection"->"Data"を開く。
- "Environment variables"の"Variable"と"Value"を入力して"Add"ボタンを押下し、環境変数を登録する。ここでは以下のようにした。
  - Variable: PUTTY_OK
  - Value: 1

## OpenSSHサーバの設定

- /etc/ssh/sshd_configを開く。
- 以下の設定を記述する。複数の設定をする際はスペースで区切って並べる。詳しくはman sshd_configを参照の事。
  - AcceptEnv PUTTY_OK

## 補足：サーバだけで環境変数を設定するには？

- PermitUserEnvironmentを設定する。
