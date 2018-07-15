# svnserveサーバ

## svnserve設定・アカウント作成

```bash
cd /var/svn/repos
vi svnserve.conf
```

```bash
[general]
anon-access = none
password-db = passwd
```

```bash
vi passwd
```

```bash
[users]
taro = taro_passwd
```

## iptables 設定

```bash
vi /etc/sysconfig/iptables
```

```bash
-A INPUT -i eth1 -m state --state NEW -m tcp -p tcp --dport svn -j ACCEPT
```

```bash
service iptables restart
```

## svnserve 起動設定

```bash
vi /etc/sysconfig/svnserve
```

```bash
OPTIONS="-r /var/svn/repos"
```

## svnserve 起動

```bash
chkconfig --add svnserve
chkconfig svnserve on
chkconfig --list | grep svnserve
```

## 動作確認

```bash
svn ls --username taror svn://localhost/
```

## 参考

http://www.ochounos.com/#blog/10
