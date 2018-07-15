# netstat - ネットワーク統計情報の表示

## あるポートを使用しているアプリケーションを調べる

```powershell
netstat -aon | findstr ":443" # ここではポート443を調べる
tasklist /fi "PID eq 9999"    # 上の結果見つかったPID9999がどのアプリケーションか調べる
```

## 参考
http://www.atmarkit.co.jp/ait/articles/0207/20/news003.html
