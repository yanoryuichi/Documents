# CentOSでユーザーコミュニティリポジトリを使う

## PostgreSQLコミュニティレポジトリ設定ファイルの追加

```clike
wget http://yum.postgresql.org/9.3/redhat/rhel-6-i386/pgdg-centos93-9.3-1.noarch.rpｍ
rpm -ivh pgdg-centos93-9.3-1.noarch.rpm
```

http://yum.postgresql.org/repopackages.php

## 標準レポジトリ設定ファイルの修正して標準パッケージのPostgreSQLをインストールから除外する

```clike
vi /etc/yum.repos.d/CentOS-Base.repo
```

```clike
[base]
（略）
exclude=postgresql*

[updates]
（略）
exclude=postgresql*
```

### 標準パッケージが除外された事を確認する

```clike
yum info postgresql-server
```

見つからなければOK。

### 補足：どのレポジトリを修正するか?

```clike
yum search postgresql
yum info postgresql-server
```

上の結果で"Repo: updates"と"Repo: base"を確認して、/etc/yum/repos.d/以下の該当箇所を探す。

## PostgreSQLのインストール
### パッケージ名の確認

```clike
yum search postgresql
```

### パッケージのインストール

```clike
yum install postgresql93-server
```

## 参考
http://lets.postgresql.jp/documents/tutorial/yum/yum
