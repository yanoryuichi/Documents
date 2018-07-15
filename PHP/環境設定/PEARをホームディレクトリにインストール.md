# PEARをホームディレクトリにインストール

## 目的
$HOME/pearディレクトリ以下にPEARのパッケージをインストールしたい。

## 設定ファイルを作る

```bash
pear config-create $HOME .pearrc
```

ホームディレクトリ以下にpearというディレクトリと.pearchファイルが出来る。


## パッケージをインストールしてみる

```bash
pear channel-discover pear.hawklab.jp
pear install hawklab/Jsphon
```

これでpear/php/Jsphonディレクトリ以下にインストールされた。

## インストールコマンドについては
http://pear.plus-server.net/installation.cli.html
