# Windowsインストール

## インストール

- 以下のウェブページを開く。
  - http://php.net/downloads.php
- [Windows downloads] から [VC11 x86 Thread Safe]を選んでダウンロードする。
  - Non Thread SafeはIISで使う。詳しくは別ページを参照すること。
- ZIPファイルを展開して、適当な場所に設置する。
  - ここではC:\phpに設置した。

## 設定

### PHP.INI

- php.ini-developmentをコピーして、php.iniというファイルを作る。
- php.ini-productionはエラー情報が非表示になっているなど、本番環境向けの設定ファイル。
- php.iniを編集する。ここでは以下のようにextensionを有効にした。

```ini
extension=php_openssl.dll
extension=php_pdo_pgsql.dll
extension=php_pdo_sqlite.dll
extension=php_pdo_mysql.dll
```

### PHPの動作確認

```bash
C:\php>php.exe -v
PHP 5.6.30 (cli) (built: Jan 18 2017 19:48:22)
Copyright (c) 1997-2016 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2016 Zend Technologies
```


## 参考
http://php.net/manual/ja/install.windows.manual.php
