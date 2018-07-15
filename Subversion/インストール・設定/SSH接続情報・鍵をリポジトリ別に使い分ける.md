# SSHのポートを指定する

## 概要

- 通常、SSH接続でSVNリポジトリにアクセスする場合、URLは svn+ssh://192.168.0.1/var/myrepo1 のようになる。
- この192.168.0.1というサーバに対してSSH接続情報や鍵を他のサーバと使い分けたい場合は以下のようにする。
- Subversionの設定ファイルに、そのサーバ向けのトンネルを作る。（例えば、ssh_myrepos1 など）
- そのサーバのリポジトリにアクセスする場合は、URLに上で作ったトンネルを指定する。

## configファイルの場所

### Windows

```bash
%appdata%\Subversion\config
C:\Users\USERNAME\AppData\Roaming
```

### UNIX系OS

```bash
$HOME/.subversion/config
```


## トンネルの作成

### Windowsでplinkを使う場合の例

```bash
[tunnels]
mytun1 = C:/Program Files/TortoiseSVN/bin/TortoisePlink.exe -l taro -pw mypass -i C:/Users/taro/Documents/myserv.ppk 
```

または

```bash
[tunnels]
mytun1 = C:\\Program Files\\TortoiseSVN\\bin\\TortoisePlink.exe -l taro -pw mypass -i C:\\Users\\taro\\Documents\\myserv.ppk 
```

### UNIX系OSでOpenSSHを使う場合の例

```bash
[tunnels]
mytun1 = ssh -q -p 12345 -i ~/.ssh/myserv.key.pem
```

## アクセス

```bash
svn ls svn+mytun1://192.168.0.1/var/myrepo1
```

## 補足

- リポジトリごとにSSH接続情報・鍵を分けず、特定の接続方法を指定するだけで良いなら、環境変数SVN_SSHにplink.exeやsshコマンドを指定してもよい。
- トンネルをいちいち作りたくない場合、WindowsならPuTTYの設定、UNIX系OSならOpenSSHの~/.ssh/configの設定をしておいて、その接続情報をURLで指定してもよい。

## 参考

- http://unix.stackexchange.com/questions/27143/how-to-configure-svn-ssh-with-ssh-on-non-standard-port
- http://wiki.netbeans.org/FaqSubversionSSH
