# ローカルPCでPuTTYのRemoteCommandを使う

## 目的
ローカルPCからremote1.comを介してremote2.comにアクセスしたい。

## 前提

```
[WindowsPC/PuTTY]
 ↓
[remote1.com/OpenSSH]
 ↓
[remote2.com/OpenSSH]
```

- ローカルPCはWindows、remote1/remote2のサーバはOpenSSHのインストールされたUNIX系OSとする。
- ローカルPCのターミナルソフトはPuTTYとする。


## 手順
### SSHアカウントの設定

- SSHのアカウント登録・公開鍵登録を以下のようにする。
  - ローカルPCの公開鍵をremote1のauthorized_keysに登録しておく。
  - remote1の公開鍵をremote2のauthorized_keysに登録しておく。

### PuTTYの設定

- PuTTYを起動して、PuTTYの設定画面を開き、通常の接続設定を行う。次に以下のような設定を行う。
  - 「セッション」 
     - 「ホスト名（またはIPアドレス）」を「remote1.com」にする。
  - 「接続」→「データ」 
     - 「自動ログインのユーザ名」を「remote1のユーザ名」にする。
  - 「接続」→「プロキシ」 
     - 「プロキシのタイプ」を「なし」にする。
     - 「Telnetコマンドまたはローカルプロキシコマンド」を「nc %host %port\n」にする。なお、remote1にはncコマンド（またはconnectコマンドなど）をインストールしておくこと。
  - 「接続」→「SSH」 
     - 「リモートコマンド」を「ssh remote2.com」にする。（必要に応じてsshコマンドのオプションを設定する。）
  - 「接続」→「SSH」→「認証」 
     - 「認証のためのプライベートキーファイル」をローカルPC内にある秘密鍵ファイルに指定する。
- 接続設定を保存する。
