# Dante Server

## インストール
### CentOS

```
yum install --enablerepo=rpmforge dante-server
```

## 設定
### /etc/sockd.conf

```
#errorlog: /var/log/socks/sockd.errlog
logoutput: /var/log/socks/sockd.log
internal: eth0 port = 1080
external: eth0
#user.privileged: root
user.unprivileged: nobody
method: username
debug: 0

client pass {
    from: 10.0.0.1/32 port 1-65535 to: 0.0.0.0/0
    log: error connect disconnect
}

pass {
    from: 10.0.0.1/32 to: 0.0.0.0/0
    log: error connect disconnect
}

client pass {
    from: .example.net port 1-65535 to: 0.0.0.0/0
    log: error connect disconnect
}

pass {
    from: .example.net to: 0.0.0.0/0
    log: error connect disconnect
}

block {
    from: 0.0.0.0/0 to: 0.0.0.0/0
    log: error connect disconnect
}
```

「10.0.0.1/32」「.example.net」は接続を許可する（クライアントPCなどの）IPアドレス。

## ブラウザのSOCKS5 authentication
IE、Firefox、Chrome等の主要なブラウザはSOCKS5 authenticationに対応していない。よって事実上method=none以外の設定は出来ない。
### 参考
http://serverfault.com/questions/267088/setting-up-dante-socks-server

## 参考

[公式] Minimal server configuration 
: http://www.inet.no/dante/doc/1.4.x/config/server.html

[公式] sockd.conf 
: http://www.inet.no/dante/doc/1.4.x/sockd.conf.5.html
