#TortoiseSVNでSSHの鍵を指定

## PuTTYをインストールする
http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html

## puttygen.exeを起動する

- "generate"ボタンを押して、マウスを適当に動かす。
- "save public key"ボタンと"save private key"ボタンを押して、鍵を保存する。マイドキュメントなど分かる場所に保存する。
- ウィンドウ上部のOpen SSH用の公開鍵を選択してコピーする。

## Suversionのリポジトリがあるサーバにログインする
先ほどコピーした公開鍵をauthorized_keysファイルにペーストして保存する。

```bash
cd $HOME/.ssh
vi authorized_keys
```

## Windowsに戻る
### TortoiseSVNの設定をする

- 適当なフォルダを右クリックして、"settings"を選ぶ。
- "network"を選び、"SSH client"に以下のように入力する。
- -iの後の文字列はputtygen.exeで保存した秘密鍵。

```bash
C:\Program Files\TortoiseSVN\bin\TortoisePlink.exe -i "C:\Users\taro\Documents\ssh\id_rsa.ppk"
```

### チェックアウトする
レポジトリのURLは以下のようになる。taroはSVNサーバ上のユーザ名。192.168.0.1はSVNサーバのIPアドレス。

```bash
svn+ssh://taro@192.168.0.1/var/svn/work
```
