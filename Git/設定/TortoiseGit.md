# TortoiseGit

## 公式サイト

https://tortoisegit.org/

## インストール方法

- 事前にGit for Windowsをインストールしておく。TortoiseGitはUIのみ提供し、Git本体はGit for Windowsのgit.exeを利用する。
- 詳しくは：https://tortoisegit.org/support/faq/


## ファイルエクスプローラーのオーバーレイアイコンをTortoiseSVNと共有

```bash
PS C:\> cd HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ShellIconOverlayIdentifiers
PS HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ShellIconOverlayIdentifiers> dir
```

- 上のコマンドで確認できように、ファイルエクスプローラーのオーバーレイアイコンをTortoiseSVNと共有するので、オーバーレイアイコンが足りなくなる心配がない。（他のアプリに占有されない限りは）。
