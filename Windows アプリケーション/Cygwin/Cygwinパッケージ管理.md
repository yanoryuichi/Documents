# Cygwinパッケージ管理

## コマンドラインからパッケージをインストールするには？

- apt-cygを使う。

```
 - apt-cygはLinuxのaptやyumのようなもの。
```

- Cygwin本体をChocolateyでインストールしたならcyg-getを使う。

```
 - cyg-getはCygwinのsetup.exeを呼び出すラッパー。
```

- setup.exeをコマンドラインで使う。

```
 - オプション指定が面倒なのでbashのエイリアス機能を使うと便利。
```

### 参考

- http://superuser.com/questions/214831/how-to-update-cygwin-from-cygwins-command-line
- http://stackoverflow.com/questions/9260014/how-do-i-install-cygwin-components-from-the-command-line/23143997#23143997

## apt-cyg

- https://github.com/transcode-open/apt-cyg
- 他にもフォークされたバージョンが存在する。


## cyg-get
### cyg-getのインストール

```
choco install cyg-get
```

### cyg-getを使ってパッケージのインストール

```
cyg-get diffutils perl
```

### cyg-getのヘルプ

```
cyg-get /?
```

- https://chocolatey.org/packages/cyg-get
- https://github.com/chocolatey/chocolatey-coreteampackages/tree/master/packages/cyg-get

## パッケージ検索
http://cygwin.com/cgi-bin2/package-grep.cgi

## パッケージ一覧
http://ftp.jaist.ac.jp/pub/cygwin/x86_64/release/
