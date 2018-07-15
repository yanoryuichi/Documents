# openfiles - オープンされてるファイルの操作

## 準備 - システム グローバル フラグ 'maintain objects list' を有効にする。

```powershell
openfiles /local on
```

この後、PCを再起動する。一度フラグを有効にすれば再度行う必要はない。

## オープンしているファイルの一覧

```powershell
openfiles 
```

## オープンしているファイルを閉じる
### IDを調べる

```powershell
openfiles.exe | find "1.txt"
  => 3704  explorer.exe         C:\Users\taro\Documents\tmp\1.txt
```

### IDを指定してファイルを閉じる

```powershell
openfiles.exe /disconnect /id 3704
```
