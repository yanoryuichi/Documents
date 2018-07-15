# Dokan SSHFS

## Dokan SSHFSとは

DokanライブラリのGUIラッパーツール。

## 公式
http://dokan-dev.net/

## インストール

- http://dokan-dev.net/download/から
- Dokanライブラリをダウンロードしてインストールする。
- Dokan SSHFSをダウンロードして、適当なフォルダに解凍する。

## 使い方

- DokanSSHFS.exeを起動する。
- ホスト名やユーザ名を指定する。
  - 秘密鍵を使う場合、OpenSSH形式のものを使う。
  - PuTTY形式の秘密鍵からOpenSSH形式の変換にはPuTTYgenを使う。http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
  - FileメニューのLoad private keyを実行しローカルの秘密鍵を選び、ConversionsメニューのExport OpenSSH keyを実行する。
- Windowsのドライブにリモートサーバが出来る。
- 終了はタスクトレイのアイコンをクリックして終了を選ぶ。
