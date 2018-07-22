# DB接続をkillする

## DB名とプロセスIDを視認してkillする

```clike
$ ps auxww|grep 'postgres:'
postgres  8794   0.0  0.1  2461712   2264   ??  Ss    9:56PM   0:00.00 postgres: taro my_db ::1(56209) idle  
$ kill 8794
```

上はmy_dbへの接続をkillする場合。

## DB名を指定して一括でkillする

```clike
for pid in $(ps -eo pid,args | grep 'postgres:' | grep my_db | tr -s ' ' ',' | cut -f 1 -d,); do
  echo kill $pid
done
```
