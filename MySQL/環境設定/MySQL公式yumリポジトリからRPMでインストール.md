# MySQL公式yumリポジトリからRPMでインストール

## MySQL公式yumリポジトリの設定

### yumリポジトリ設定パッケージの取得とインストール

- 以下のURLを開く。
  - http://dev.mysql.com/downloads/repo/yum/
- パッケージ一覧のリンクがあるので、自分のOSにあったパッケージを探して、Downloadボタンを押下する。
  - 今回はOSをCentOS 7とする。Red Hat Enterprise Linux 7 / Oracle Linux 7 (Architecture Independent), RPM Package を選んだ。
- "Begin Your Download"というダウンロードを開始する画面が表示される。Oracleのアカウントを要求されるが、アカウントを作らなくてもダウンロードできる。LoginボタンやSign Upボタンではなく、"No thanks, just start my download."というリンクを押下する。
- RPMパッケージをダウンロードしたら、rpmコマンドでインストールする。

```clike
wget http://dev.mysql.com/get/mysql57-community-release-el7-7.noarch.rpm
sudo rpm -ivh install mysql57-community-release-el7-7.noarch.rpm
```

### yumリポジトリ設定の修正

- RPMパッケージをインストールすると、デフォルトでいくつかのリポジトリが有効になっている。
  - /etc/yum.repos.d/mysql-community.repo
  - /etc/yum.repos.d/mysql-community-source.repo
- 必要に応じて無効にするなどする。
- 無効にするには上のファイルの"enabled=1"の行を"enabled=0"にする。
- どのリポジトリ（サブリポジトリ）が有効・無効になっているかは以下のコマンドで確認する。

```clike
yum repolist all | grep mysql
```

## MySQLのインストール

### リポジトリを指定してMySQLパッケージを検索

```clike
yum search --enablerepo=mysql57-community mysql
```

### リポジトリを指定してMySQLパッケージをインストール

```clike
yum install --enablerepo=mysql57-community mysql-community-client \
  mysql-community-common mysql-community-devel mysql-community-server
```

## MySQLサーバの起動

```clike
sudo systemctl start mysqld.service   # 起動（CentOS 7）
sudo systemctl status mysqld.service  # 起動確認（CentOS 7）
```

## rootパスワードの設定
### 現在のパスワードの確認

```clike
sudo grep 'temporary password' /var/log/mysqld.log
```

### MySQLサーバへログインしてパスワードを変更（ポリシー変更）

```clike
mysql -uroot -p

mysql> SET GLOBAL validate_password_length=6;
mysql> SET GLOBAL validate_password_policy=LOW;
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'testtest'
```

## 参考
http://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/
