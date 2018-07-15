# PuTTYのダイナミックポートフォワードを使う

## 手順
### remote1サーバへの接続セッションを作る

- remote1サーバへ普通に接続出来るように設定する。
- 設定メニューの"Connection"→"SSH"→"Tunnels"を開く。
- 以下の2つの項目の設定をする。
  - Source port: 10022
  - Dynamic: チェックする
- "Add"ボタンを押下する。
- セッションを保存する。セッション名はremote1-sessとする。

### remote2サーバへの接続セッションを作る

- remote2サーバへ普通に接続出来るように設定する。
- 設定メニューの"Connection→"Proxy"を開く。
- 以下の3つの項目の設定をする。
  - Proxy type: SOCKS 5にチェックを入れる。
  - Proxy hostname: localhost
  - Port: 10022
- セッションを保存する。セッション名はremote2-sessとする。

### remote1サーバへダイナミックポートフォワードをしてSOCKSプロキシを作る

```
plink.exe -N -load fumidai-sess
start /B plink.exe -N -load remote1-sess
```

### SOCKSプロキシを経由してremote2サーバへ接続する

- remote2-sessを使ってremote2サーバへの接続を確認する。
