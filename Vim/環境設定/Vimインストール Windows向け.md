# Vimインストール Windows向け

## 概要

- vim.orgからWindows向けのVimを入手してインストールする
- 日本ではKaoriyaのVimを使っている人も多いと思うが、普通に本家のvim.orgのVimでいいと思う

## インストーラーの入手

- 以下のvim.orgからWindows向けのMSIインストーラー（exeファイル）をダウンロードする
- https://www.vim.org/download.php


## インストーラーの実行

- exeファイルをダブルクリックして、ウィザードを起動する
- インストールオプションを指定するが、そのままでよいと思うが、今回は”Create icons on the desktop"のチェックを外した。次へ。
- Key mappingとMouse behaviorを選択できるが、Defaultでいいと思う。多分、あとで.vimrcなどで設定可能だと思う。次へ。
- インストール先のフォルダーの指定。デフォルトでは、C:\Program Files (x86)\Vim だけれど、変えた方が無難な気がする。将来的にVim以下に設定ファイルなどを作ることを考慮すると、C:\Program Filesのような書き込みに特権が必要なフォルダーは避けた方がいい。今回はC:\Vimにする。Installボタンを押下。
- インストールが終わったら、Closeでウィザードを閉じる。

## Vimの初期設定

### インストール先のファイル構成

```clike
C:\Vim\
  vim81\  # vim.exeやgvim.exeのような本体の実行ファイル、autoloadやcolorsのようなランタイム、設定フォルダーが含まれる
  _vimrc  # デフォルトの設定ファイル（Unix系の.vimrc相当）
```

### コマンドサーチPathの設定

```clike
PS> cmd
CMD> setx PATH "%Path%;C:\Vim\vim81"
```

- デフォルトではPathに追加されてないので、自分で追加する。追加しなくても使えるが、WindowsでもVimはコマンドラインから起動することが多いので、追加する方がいいだろう。
- ちなみに、C:\VimをPathに加えるより、vim.exeやgvim.exeのラッパーBatを別の場所に作って、そのBatをPathに加える方がいいかもしれない。今回は面倒なのでしない。
- PowerShellから設定するには、上のようにする。（しかし、なぜPowerShellには環境変数を設定するコマンドレットがないんだろう？）
- もしくはWIN+Sキーを押して、sysdm.cpl と入力して、システムの詳細設定->環境変数を開き、Pathに追加する。
- タスクマネージャーを起動して、エクスプローラーを再起動する。もしくはPCを再起動する。環境変数がシェルに反映されるので、PowerShellを起動して、gvim.exe と入力して、Vimが起動するのを確認する。


### vimrcファイルの読み込み場所の確認

```clike
:version
```

- Vimを起動して、:versionでvimrcの読み込み順を確認する。

### vimrcファイルの設置

- 上の読み込み場所の確認で分かるように、C:\Vim\_vimrcかC:\Vim\Vimfiles\_vimrcにファイルを作るのがよいだろう。（加えて、_gvimrcも）
- インストール時に作成された_vimrcファイルは削除するか、リネームして退避させておく。
