# CentOSで外部リポジトリからインストールする

## 概要

- CentOSの標準のPHPはバージョンが古いので、外部リポジトリからPHPをインストールする。
- PHP公式サイト（http://jp2.php.net/downloads.php）ではRemiとIUSという2つの外部リポジトリがリンクされている。
- 今回はRemiリポジトリを使う。
- なお、CentoSは6、PHPは5.5とする。

## Remiリポジトリ（とEPELリポジトリ）の追加
### EPELリポジトリの追加

```bash
rpm -ivh http://ftp.iij.ad.jp/pub/linux/fedora/epel/6/i386/epel-release-6-8.noarch.rpm
```

http://fedoraproject.org/wiki/EPEL

### Remiリポジトリの追加

```bash
rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
```

### 参考
http://blog.famillecollet.com/pages/Config-en

## PHPのインストール

```bash
yum install --enablerepo=remi-php55 php php-cli php-common php-devel \
  php-mbstring php-mysqlnd php-pdo php-pear php-pgsql php-tidy php-xml
```

## 参考
http://www.1x1.jp/blog/index.php?s=centos
