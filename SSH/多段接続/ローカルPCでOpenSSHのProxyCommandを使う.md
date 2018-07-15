# ローカルPCでOpenSSHのProxyCommandを使う

## 目的
localhostからremote1.comを介してremote2.comにアクセスしたい。

## 前提

```
[UnixPC/OpenSSH]
 ↓
[remote1.com/OpenSSH]
 ↓
[remote2.com/OpenSSH]
```

- localhost/remote1/remote2、全てのサーバ（ホスト）はOpenSSHのインストールされたUNIX系OSとする。
- remote1/remote2のFQDNは以下の通りとする。
  - remote1.com
  - remote2.com
- remote1/remote2のユーザ名は以下の通りとする。
  - remote1: user-remote1
  - remote2: user-remote2
- 公開鍵の登録を以下の通りにしておく。
  - localhostの公開鍵をremote1のauthorized_keysに登録しておく。
  - localhostの公開鍵をremote2のauthorized_keysに登録しておく。

## 手順
1. connectコマンドをremote1.comにインストールする。

```bash
wget http://www.meadowy.org/~gotoh/ssh/connect.c
gcc connect.c -o connect
cp connect $HOME/bin/
```

nc(netcat)コマンドでも良い。http://netcat.sourceforge.net/

2. localhostの$HOME/.ssh/configを以下のようにする。

```
Host remote2.com
user user-remote2
ProxyCommand ssh -l user-remote1 remote1.com /home/user-remote1/bin/connect %h %p
```


3. localhostからSSHコマンドを実行してremote2へ接続できるようになる。

```bash
ssh remote2.com
```

## 参考

- http://www.meadowy.org/~gotoh/projects/connect
- http://cl.pocari.org/2006-09-04-2.html
