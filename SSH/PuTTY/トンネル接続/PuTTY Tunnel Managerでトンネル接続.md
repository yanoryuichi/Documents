# PuTTY Tunnel Managerでトンネル接続

## PuTTY Tunnel Manager とは？
PuTTYのplink.exeを使ってリモートのSSHサーバとトンネルを張り、そのセッションをWindowsのタスクトレイで管理出来るようにする。

## PuTTY Tunnel Managerのインストール

- 以下のURLからptman.exeをダウンロードする。
  - http://code.google.com/p/putty-tunnel-manager/
- ptman.exeをPuTTYがインストールされたフォルダーにコピーする。

## ローカルホストのSSHポートをリモートホストのSSHポートへ転送してSSH接続する
### PuTTY Tunnel Managerの起動と設定

- ptman.exeをダブルクリックする。
- タスクトレイの黒丸のアイコンを右クリックして、[Settings...]を選ぶ。
- [General]タブを選ぶ。
  - Session name: Tunnel to linux_srv_01.com
- [SSH]タブを選ぶ。
  - Hostname: linux_srv_01.com
  - Port: 22
  - Username: taro
- [Local ports]タブを選ぶ。
  - [Add]ボタンを押下する。
     - Local port: 10022
     - Remote host: linux_srv_01.com
     - Remote port: 22
- ウィンドウを閉じる。
- タスクトレイのアイコンを右クリックして、[Tunnels...]を選び、[Tunnel to linux_srv_01.com]を選ぶ。

### PuTTYの起動とSSH接続の実行

- PuTTYを起動する。
- 以下のように設定する。
  - 接続先IPアドレス：127.0.0.1
  - 接続先ポート： 10022
- この設定に対して接続する。
- linux_srv_01.comに接続できた事を確認する。
