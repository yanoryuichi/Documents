# Ping送信 - Test-Connection

```powershell
$ips = @('192.168.0.1','192.168.0.2','mypc1')
$max = 10; while ($max--) { foreach ($ip in $ips) { Test-Connection -Count 1 $ip } }
```

### Test-Connectionの注意点

- システムに負担が掛かり、遅い。
- したがって、長時間実行する場合は、Test-Connectionコマンドレットではなく、DOSのping.exeコマンドを使った方が良い。
- ping.exeの機能が足りない場合は、Sysinternalsのpsping.exeを使うといい。

## 参考

- https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.management/test-connection
- http://stknohg.hatenablog.jp/entry/2016/06/16/231239
