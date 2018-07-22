# SSHでPuTTYの接続セッションを利用する

## 概要
plink.exeのラッパーコマンドを作り、TortoiseHGのplink.exeと差し替え、ラッパーコマンド内にて必要に応じてPuTTYの接続セッションを利用するようにする。

## 手順
### 1. ラッパーコマンド作成

- 以下のコマンドをplink-wrapper.cmdとして作成し、パスの通ったフォルダに設置する。

```clike
@echo off

SET PLINK=C:\Tool\PuTTY\plink.exe
SET PPK=C:\Tool\PuTTY\mykey.ppk
 
SET ssh_url=%~1
SET keyword=%ssh_url:~0,8%
SET sessname=
if %keyword%==session- SET sessname=%ssh_url:session-=%
if not "%sessname%"=="" (
    %PLINK% -load "%sessname%" %2
) else (
  %PLINK% -batch -C -i %PPK% %*
)
```

### 2. TortoiseHgの設定

- TortoiseHg Workbenchを起動。
- ファイル→設定を開く。
- 「ファイルを開く」ボタンを押下。
- [ui]の項を以下のようにする。

```clike
[ui]
ssh =  plink-wrapper.cmd
```

## 使い方

- SSHのパスを指定する際に、ssh://session-XXX//home/repos1 のようにsession-で始まるURLを指定する。
- すると、ラッパーコマンドがPuTTYのXXXという接続セッション名を指定してplink.exeを起動する。
