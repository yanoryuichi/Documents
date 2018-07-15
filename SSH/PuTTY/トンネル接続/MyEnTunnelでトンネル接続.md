# MyEnTunnelでトンネル接続

## MyEnTunnelのインストール

- 以下のURLからZIPファイルをダウンロードする。
  - http://nemesis2.qx.net/pages/MyEnTunnel
- 適当なアプリケーションフォルダーを作成し、ZIPファイルを展開した中身をアプリケーションフォルダーへコピーする。
- （MyEnTunnelにはplinkが同梱されていないので、）アプリケーションフォルダーにplink.exeをコピーする。

## ローカルホストのSSHポートをリモートホストのSSHポートへ転送してSSH接続する
### MyEnTunnelの起動と設定

- myentunnel.exeをダブルクリックする。
- タスクトレイの鍵のアイコンを右クリックして、[Show]を選ぶ。
- [Settings]タブを選ぶ。今回は以下のように設定する。
  - SSH Server: linux_srv_01.com
  - SSH Port: 22
  - Username: user01
- [Tunnels]タブを選ぶ。今回は以下のように設定する。
  - （左側の[Local:]のテキストエリアに）10022:linux_srv_01.com:22
- [Status]タブを選ぶ。
  - [Connect]ボタンを押下する。
  - ログを見て、接続完了した事を確認する。

### PuTTYの起動とSSH接続の実行

- PuTTYを起動する。
- 今回は以下のように設定する。
  - 接続先IPアドレス：127.0.0.1
  - 接続先ポート： 10022
- この設定に対して接続する。
- linux_srv_01.comに接続できた事を確認する。

## plink.exeを指定する

- myentunnel.iniファイルをエディタで開く。
- 以下のように指定する。

```
Executable="C:\Users\taro\App\PuTTY\plink.exe"
```

- これでいいはずだが、どうも上手く動かない？

### 参考

```
Executable - Full path and name to replacement executable;normally: plink.exe
ExecArguments - For customized options;normally: -N -ssh -2
```

## 秘密鍵を指定する

- myentunnel.iniファイルをエディタで開く。
- 以下のように秘密鍵のパスを指定する。

```
FullPathKeyfile="C:\Users\taro\Documents\SSH\my.ppk"
```
