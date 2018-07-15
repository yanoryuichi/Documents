# コマンドラインでSCPする

PuTTY付属のpscp.exeを使う。

パスが通った場所にpscp.exeのシムリンクを作っておき、以下のようにして使う。

```powershell
pscp foo.txt taro@example.com:tmp/
pscp -load "EXAMPLE-COM" -ls
```

オプション-loadではputty.exeを起動した時に表示される保存されたセッション名を指定する。
