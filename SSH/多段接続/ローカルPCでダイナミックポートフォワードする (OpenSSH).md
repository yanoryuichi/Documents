# ローカルPCでダイナミックポートフォワードする (OpenSSH)

## 概要

- ローカルPCからRemote1サーバを経由してRemote2サーバにアクセスしたい。
- 以下の方法で実現する。
  - ローカルPC上にRemote1サーバにダイナミックポートフォワードするSOCKSプロキシを作る。
  - SOCKSプロキシを経由してRemote2サーバへSSH接続する。

## 各ホストの環境

- ローカルPC
  - OS UNIX/OpenSSH
  - SOCKSプロキシポート番号 10022
- Remote1サーバ
  - OS UNIX/OpenSSH
  - SSHポート番号 22
  - ユーザ名 remote1-user
- Remote2サーバ
  - OS UNIX/OpenSSH
  - SSHポート番号 22
  - ユーザ名 remote2-user

## 手順
### 1. SOCKSプロキシの作成

```bash
ssh -f -N -D 10022 -l reomote1-user -p 22 remote1.com
```

上のコマンドをローカルPC上で実行して、ローカルPC上の10022番ポートにSOCKSプロキシを作る。

### 2. SSH接続の実行

```bash
ssh -l remote2-user -p 22 -o 'ProxyCommand nc -x localhost:10022 %h %p' remote2.com
```

上のコマンドをローカルPC上で実行して、SSH接続する。
