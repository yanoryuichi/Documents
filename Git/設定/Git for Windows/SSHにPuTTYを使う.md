# SSHにPuTTYを使う

- msysgitでは、環境変数GIT_SSHが設定されていればその設定がコマンドとして実行され、設定されてなければ内蔵のSSHコマンドが実行される。
  - msysgit内蔵のSSHはOpenSSHだが、Git以外のWindowsアプリとの相互運用を考えると、OpenSSHは使わずにPuTTYを使う事を勧める。
- よって、GIT_SSHにPuTTYのSSHコマンドであるplink.exeを設定する。
- 環境変数GIT_SSHを設定するにはコントロールパネルから"システム"→"システムの詳細設定"→"環境変数"を開く。（もしくはRapid EEというフリーウェアを使うと簡単。）

```bash
GIT_SSH="C:\Users\taro\App\PuTTY\plink.exe"
```

## SSHの秘密鍵・公開鍵

- msysgitのSSHはOpenSSHなのでPuTTYのputtygen.exeを使ってOpenSSH形式の秘密鍵・公開鍵に変換しておく。
  - puttygen.exe: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
- OpenSSHの鍵作成手順
  - puttygenを起動して、
  - 秘密鍵はメニューの「変換」→「OpenSSH形式へエクスポート」で保存、
  - 公開鍵は画面上のテキストエリア「OpenSSHのauthorized_keysファイルに･･･」をコピーペーストで保存する。
- 鍵ファイルを置く場所（標準）
  - 秘密鍵： %HOME%.ssh\id_rsa
  - 公開鍵： %HOME%.ssh\id_rsa.pub

## SSHの秘密鍵の場所を指定する（SSHコマンドにオプションを指定する）
### msysgitの動作

- 環境変数GIT_SSHを以下のようにしてオプション指定して実行しようとしても動作しない。

```bash
GIT_SSH="C:\Users\taro\App\PuTTY\plink.exe -i C:\Users\taro\Documents\SSH\key01.ppk"
```

- 従って、SSHコマンドのラッパーを作り、ラッパー内でオプションを指定し、GIT_SSHにはラッパーコマンドを指定する。

### 手順

- 以下のようなラッパーコマンドを作り、"C:\Users\taro\App\PuTTY\gitssh.cmd"として保存する。

```bash
@echo off
"C:\Users\taro\App\PuTTY\plink.exe" -i "C:\Users\taro\Documents\SSH\key01.ppk" %*
```

- "C:\Users\taro\App\Git\setup.ini"を編集して、環境変数GIT_SSHをにラッパーコマンドを指定する。

```bash
GIT_SSH="C:\Users\taro\App\PuTTY\gitssh.cmd"
```

### ラッパーコマンド以外の手段： pagent.exe
pagent.exeを使って予め秘密鍵をロードして置くという手段もある。

### ラッパーコマンド修正
PuTTYのセッション名をgit clone ssh://session-server01/home/git/workみたいな感じで指定出来るよう対応した。

```bash
@echo off

SET PLINK=C:\Users\taro\App\PuTTY\plink.exe
SET PPK=C:\Users\taro\Documents\ssh\key.ppk

SET ssh_url=%1
SET ssh_url=%ssh_url:"=%
SET keyword=%ssh_url:~0,8%
SET sessname=
if %keyword%==session- SET sessname=%ssh_url:session-=%
if not "%sessname%"=="" (
    %PLINK% -load "%sessname%" %2
) else (
  %PLINK% -i %PPK% %*
)
```
