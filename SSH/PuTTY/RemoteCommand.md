# RemoteCommand

## RemoteCommandとは？

- SSHログイン後に、シェル（/bin/bash等）の代わりに実行するコマンド。
- 用途は下のようなものが考えられる。
  - "ssh another-server.com"と設定して、SSHで接続したサーバからそのまま別のサーバ（ここではanother-server.com）にSSH接続する。多段SSH接続。
  - "ps aux"と設定して、接続したサーバのプロセス情報を取得する。コマンドラインからplink.exeで接続すればリダイレクトで結果をファイルに書き込める。

## 手順
### GUIで指定する

- PuTTY Configurationダイアログを開く。
- 通常の接続設定を行う。
- "Connection"->"SSH"を選ぶ。
- "Data to send to the server"の"Remote command"に以下のようにコマンドを設定する。

```
touch 1.txt; touch 2.txt; ls -l
```

- この接続設定を開いてサーバに接続する。

### コマンドラインから指定する

- コマンドファイルを作成する：notepad.exe commands.sh

```
touch 1.txt
touch 2.txt
ls -l
```

- -mオプションを付けて、サーバに接続する。

```
plink.exe -m commands.sh 192.168.0.1
```

### 注意

- 非疑似端末モードになるので、必要に応じて、-tオプションを付けて強制的に疑似端末モードにする。

## 参考
http://the.earth.li/~sgtatham/putty/0.62/htmldoc/Chapter7.html#plink
