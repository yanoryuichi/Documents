﻿# 多段ローカルポートフォワード（PostgreSQL接続）

## 目的

- 以下のようなネットワーク環境を想定し、PCからまず踏み台サーバに接続し、そこからWebサーバに接続し、さらにそこからPostgreSQLサーバに接続する。

```
[PC] グローバルIPアドレス（非固定）
↓
[踏み台サーバ 10.0.0.1] グローバルIPアドレス
↓
[Webサーバ 10.0.0.2/192.168.0.2] グローバルIPアドレス/プライベートIPアドレス
↓
[PostgreSQLサーバ 192.168.0.3] プライベートIPアドレス
```

- PC: 非固定のグローバルIPアドレスしかない
- 踏み台サーバ: ウェブサイトサーバ群に接続する為の踏み台でどこからの接続でも許可する
- Webサーバ: 踏み台サーバからの接続のみ許可する
- PostgreSQLサーバ: プライベートIPアドレスしかなく、必ずWebサーバを介してしか接続する

## 方法
2回ポートフォワードを行う。

```bash
ssh -L 10022:10.0.0.2:22 -fN userA@10.0.0.1
ssh -L 10023:192.168.0.3:5432 -fN -p 10022 userB@localhost
```

これでPCのローカルポート10023に接続するとDBサーバの5432ポートに接続出来るようになる。

```bash
psql -U taro -h localhost -p 10023 test_db
```

### 注意

- userAは踏み台サーバ上のユーザ。
- userBはDBサーバ上のユーザ。
