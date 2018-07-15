# PECL拡張モジュールをインストールする

## 前提

- ここではJSON拡張モジュールをインストールする。
- pearコマンドはインストール済みとする。
  - PHP5.1以降はconfigureコマンドで--without-pearを指定しない限りインストールされる。
  - 入ってない場合は↓などでインストールする。

```bash
curl http://pear.php.net/go-pear > pear.php
php pear.php
```

## 手順
### モジュールインストール

```bash
pear install pecl/json
```

### 設定変更
php.ini:

```ini
extension_dir=/usr/local/lib/php/extensions/no-debug-non-zts-20050922
extension=json.so
```
