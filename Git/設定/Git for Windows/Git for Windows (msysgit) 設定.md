# Git for Windows (msysgit) 設定

## git statusで日本語ファイル名を表示可能にする
以下のコマンドを実行する。

```bash
git config --global core.quotepath false
```

なお、日本語のファイル名のファイルをコミットして、ファイル名を確認するまでの手順は以下の通り。

```bash
mkdir git.test.repos
cd git.test.repos
git init
echo "HELLO" > 日本語.txt
git add 日本語.txt
git commit -m 'japanese filename test'
git ls-files
```

## git commitで使うエディタを変更する

- デフォルトではvimだが、以下のようなコマンドを実行して、好みのエディタに変更する（今回はgvim.exe）。
  - なお、Windows 8以降ではコマンドプロンプトの仕様変更によりコンソール版のvimは正常に日本語入力出来ないので（2014/1現在）、別のエディタを使うしかない。
- 但し、改行コードの自動判別機能、UTF8保存機能等が必要で、エディタによっては上手く動かないので、諦めてvimの使い方を覚えるか、git commit -m 'コミットのコメント'で直接コメントを指定するか。

```bash
git config --global core.editor "gvim.exe --nofork -c 'set fenc=utf8'"
```

## 環境変数HOME

- .gitconfig等の設定ファイルの保存場所はデフォルトで%USERPROFILE%だが、環境変数HOMEによって指定出来る。
  - Windowsではユーザ設定ファイルは%APPDATA%以下に置く事が推奨されている。
- 環境変数HOMEはコントロールパネルのシステム環境変数で指定するか、Gitのみに適用するにはGitインストールフォルダ以下のgit.cmd（C:\Users\taro\App\Git\cmd\git.cmd等）をテキストエディタで開き、先頭行に以下のような記述を加える。

```bash
@set HOME=%USERPROFILE%\Documents\Git
```

  - 但し、最近のGitはgit.cmdが存在しないようで、その場合はgit.comを以下のように自分で作る。

```bash
@set HOME=%USERPROFILE%\Git
C:\Users\taro\App\Git\cmd\git.exe %*
```

- 次にマイドキュメント以下にGitフォルダを作れば、Gitの設定ファイル等はここを参照するようになる。
- なお、Gitを利用する際はgit.exeではなくgit.cmdを実行するようにサーチパスを工夫する事。
  - PowerShellでは.cmdより.exeの方が優先順位が高い？ようなので、git.cmdでなくgit.comで作ると良さそう。

## GIT_TRACE

Gitコマンドの動作をトレースするには以下のようにPowerShell上で環境変数GIT_TRACEを指定する。

```bash
$env:GIT_TRACE=1
```

## 改行コードの自動変換

```bash
git config --global core.autocrlf false
git config --global core.autocrlf input
```

### input
> この設定は、Windows にチェックアウトしたときの CRLF への変換は行いますが、Mac や Linux へのチェックアウト時は LF のままにします。またリポジトリにコミットする際には LF への変換を行います。

- http://git-scm.com/book/ja/v1/Git-%E3%81%AE%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%9E%E3%82%A4%E3%82%BA-Git-%E3%81%AE%E8%A8%AD%E5%AE%9A

## ロングファイルパスの制限解除（MAX_PATH)

```bash
git config --global core.longpaths true
```

- https://github.com/git-for-windows/git/commit/a789c7195835bd9e57f6a4a2889f0a8132902285
- http://stackoverflow.com/questions/4992577/msys-git-and-long-paths
