# 環境変数SVN_SSHにSSH接続方法を指定する

- SSH経由でリポジトリにアクセスする場合に、特定の鍵を指定したりユーザ名を指定するなど、SSH接続方法を指定したい場合、環境変数SVN_SSHを設定する。
- SVN_SSHは環境変数でもよいし、Subversionの設定ファイルに記述してもよい。

### コマンドラインで環境変数を指定

```bash
[Windowsの例]
set SVN_SSH="C:/Program Files/TortoiseSVN/bin/TortoisePlink.exe" -l taro -i C:/ssh/my.ppk 
```

```bash
[UNIX系OSの例]
export SVN_SSH="ssh -l taro -i ~/.ssh/my.key.pem"
```

### Subversionの設定ファイルで指定

- Windowsの場合、設定ファイルは%appdata%\Subversion\config にある。
- 以下のように記述する。

```bash
[tunnels]
ssh = $SVN_SSH "C:/Program Files/TortoiseSVN/bin/TortoisePlink.exe" -l taro -i C:/ssh/my.ppk
```

## 参考

- http://www.pushok.com/help/svnscc/adv/svnssh.html
- http://stackoverflow.com/questions/16214136/how-to-use-svnssh-with-tortoise-svn-from-the-command-line
