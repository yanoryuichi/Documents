# PuTTYのセッションを使ってSSH接続する

## 1. 前提・準備

- TortoiseSVNは、TortoisePlink.exeが同梱されており、標準ではこれを使ってSSH接続する。
  - C:\Program Files\TortoiseSVN\bin\TortoisePlink.exe
- TortoiseSVNのTortoisePlink.exeはPuttyのplink.exeとセッションを共用できる。
- したがって、普段、PuTTYを使ってSSHを利用しているなら、TortoiseSVNでもPuTTYのセッションを共用すると便利が良い。
- ただし、PuTTYは、INIファイルではなく、レジストリに設定を保存するPuTTYを用意する。

## 2. PuTTYの設定

- PuTTYを起動して、SVNサーバに接続する設定を作り、セッションとして保存する。
- ここではmy-svn-sessというセッション名とする。

## 3. TortoiseSVNの設定

- ファイルエクスプローラーを起動して、適当なスペースを右クリックして、[TortoiseSVN] -> [Settings]を選ぶ。
- Settingsウィンドウが開くので、左ペインより[network]を選び、中の[SSH client]に以下のように入力する。（もしくはBrowseボタンを押下して、TortoisePlink.exeを探して選ぶ。）
- C:\Program Files\TortoiseSVN\bin\TortoisePlink.exe

## 4. TortoiseSVNによるSSH経由のリポジトリアクセス

- ファイルエクスプローラーを起動して、適当なスペースを右クリックして、[TortoiseSVN] -> [Repo-browser]を選ぶ。
- URLを促すダイアログが開くので、以下の例のように入力する。
  - ここでは、
  - セッション名 my-svn-sess
  - SVNサーバ上のパス /var/sv/my-repos
- セッション名にスペースが含まれていると正常に動作しないようだ。スペースの代わりに-などの文字に置き換えてセッションを保存しなおす。

```bash
svn+ssh://my-svn-sess/var/svn/my-repos
```

## 補足 INIファイルを使うPuTTYのセッションを利用したい場合

- 多分、TortoiseSVNのTortoisePlink.exeはINIファイルに対応してない。
  - TortoisePlink.exeの全オプションは、コマンドラインから C:\Program Files\TortoiseSVN\bin\TortoisePlink.exe を実行すると表示される。
- なので、TortoiseSVNのSettingsで、自分でインストールしたINIファイル対応のplink.exeを指定する。
- これで、TortoiseSVNでSSH接続すると、そのplink.exeが呼び出される。
- が、その際にセッション情報を保存してあるINIファイルを読んでくれるかどうかは、そのplink.exeの実装次第だと思う。未検証なので分からない。
- それにPuTTYのplink.exeはSVNがプロセスが作るたびにDOSウィンドウが開くので、かなり見た目が悪い。
  - http://tortoisecvs-users.narkive.com/degE1ai3/plink-vs-tortoiseplink
  - https://svn.haxx.se/tsvnusers/archive-2006-05/0234.shtml

## 参考

- https://tortoisesvn.net/ssh_howto_logemann.html
- https://the.earth.li/~sgtatham/putty/0.67/htmldoc/
- https://tortoisesvn.net/docs/release/TortoiseSVN_ja/index.html
