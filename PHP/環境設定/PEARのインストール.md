# PEARのインストール

```bash
curl https://pear.php.net/go-pear.phar -o go-pear.phar
php go-pear.phar
```

- 事前にPHPをインストールしてPATHを通しておく。pear.iniファイルが存在することも確認しておく。
- go-pear.pharをダウンロードして、実行する。
- CLIのインストーラーが起動する。
- システムワイドなインストールをするか聞かれるので、エンターキーでsystemを選ぶ。
- インストール場所を変える場合、メニューの1.を選び、"C:\PEAR"などにする。
  - Windowsの場合、C:\PEAR\\tmp のようにバックスラッシュが重なるが気にしなくていい。
- pear.iniを変えるなら、$prefix\pear.ini のようにする。
- pear（またはpear.bat）のあるディレクトリ（ここではC:\PEAR）を環境変数PATHに加える。このディレクトリにPEARでインストールするパッケージに付属するコマンドがインストールされていく。

## 参考

https://pear.php.net/manual/en/installation.getting.php
