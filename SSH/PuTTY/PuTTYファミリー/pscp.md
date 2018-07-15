# pscp

pscp.exeを使ってscpを実行できる。以下はPuTTYで DEV-srv01 として保存済みのセッションのサーバからファイル（ディレクトリ）をコピーする例。

```
pscp.exe -r DEV-srv01:tmp/ .
```

## 参考
http://the.earth.li/~sgtatham/putty/0.62/htmldoc/Chapter5.html#pscp
