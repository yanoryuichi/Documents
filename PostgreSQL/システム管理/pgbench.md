# pgbench

## インストール
### CentOS6

```clike
yum install postgresql-contirb
```

## 使用方法
### DBの準備

```clike
createdb testdb01
pgbench -i -s 10 testdb01
```

- -s　スケールファクターN*10万行のレコードを用意
- -i　初期化

### ベンチマーク実行

```clike
pgbench -S -c 10 -t 1000 testdb01
```

- -c　同時接続数
- -t　トランザクション数

## 参考
http://www.techscore.com/tech/sql/pgbench/index.html/
