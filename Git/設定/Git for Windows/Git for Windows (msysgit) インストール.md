# Git for Windows (msysgit) インストール

## インストール方針

- Git for Windows (旧称msysgit、以下Git)はMinGW+MSYS環境下で動作し、Gitの本体であるgit.exeはMSYSコマンド群の1つとして構成される。
- GitはGit Bash上かコマンドプロンプト（PowerShell）上でgit.exe(git.cmd)コマンドを実行して使用する。CUIのコンソールアプリケーションであり、GUIはない。
  - Windows向けのGUIアプリは、SourceTreeやGit Extensions等がある。いずれもGUIラッパーで、内部ではGitを呼んでいる。
- Git Bash上ではMSYSによるUNIX系コマンド群を併用出来るが日本語対応が面倒なのとGit Bashという特殊なシェル環境をメンテナンスしくたくないので、今回はPowerShell上で使う事を前提にする。
  - 今回はC:\App\Gitにインストールする。
  - 標準構成のC:\Program files以下はUACで権限を昇格しないと書き込みが出来ないので、Gitのような細かい設定をユーザ自らテキストエディタ等で編集しがちなアプリには適切でないと思う。
- なお、すでにWindowsにMinGW+MSYSをインストール済みでもGitは別にインストールする。その方が余計なトラブルがなくて良い。

## インストール手順

- 以下から最新版のインストーラーをダウンロードする。
  - https://git-for-windows.github.io/
- インストーラーを実行する。
- インストール先を以下にする。

```bash
C:\Users\taro\App\Git
```

- [Select components]オプションのチェックを全部外す。
  - エクスプローラーのコンテキストメニュー拡張を使いたい場合は[Windows Explorer integration]にチェックを入れる。が、コンテキストメニューが鬱陶しくなるので今回は入れない。
- [Adjusting your PATH enviroment]オプションは[Run Git from the Windows Command Prompt]を選ぶ。
  - [Run Git and included Unix tools from the Windows Command Prompt]はUNIX系コマンド群がWindows標準コマンドを上書き混乱を招くので選択しない事を勧める。
- [Choosing the SSH executable]オプションは、
  - すでにPuTTYを使っていてPuTTYのセッション設定がレジストリにあるなら[Use Plink]を選んで、PuTTYインストールフォルダ内のplink.exeを設定する。
  - そうでないなら[Use OpenSSH]を選ぶ。
  - 今回はPlinkを選んだ。WindowsでSSHを使うならPuTTYに依存する事が多いので。
  - 但し、OpenSSHにせよ、PuTTYにせよ、SSHクライアントのラッパーコマンドを作って、それを環境変数GIT_SSHで指定する、というやり方が柔軟な使い方が出来て良いと思う。
- [Configuring the ending conversions]オプションは[Checkout as-is, commit Unix-style line encodings]を選ぶ。
  - LFなソースコードをCR+LFに変換してローカルにチェックアウトするメリットとして、WindowsのExplorer（のようなLF非対応アプリ）からでも検索が可能になるというのがある。
  - 但し、Windows用のLF対応Grepアプリをローカルにインストールしてそれを使う方が良いように思う。CR+LFにすると動かなくなるUnix上の処理系は多い。
  - メモ帳のようなLF非対応アプリからテキストファイルを新規作成する事がないのなら、[Checkout as-is, commit as-is]にしても良いだろう。
- [Configuring the terminal emulator to use with Git Bash]オプションはは[Use MinTTY]を選ぶ。
  - Git Bashを使う場合はMinTTYからの方が良いでしょう。
- [Configuring experimental performance tweaks]
  - [Enable file system caching]
  - https://github.com/msysgit/msysgit/wiki/Diagnosing-why-Git-is-so-slow 等を参考にすると良いのかも？
- インストールを完了する。
- 環境変数の反映の為、エクスプローラーを再起動するかWindowsにサインインし直す。

## Chcocolateyを使ってインストールする（インストール先ディレクトリを指定する）

```bash
CMD> choco install git.install -o -ia '/DIR="C:\App\Git"'
```

- 事前にC:\App￥Gitフォルダをを作成しておく。
- コマンドプロンプトから上記を実行すると、Gitをダウンロード後、インストーラーが起動する。その際、インストール先はC:\App\Gitになっている。それ以外については上の説明に従ってインストール作業を完了させる。
