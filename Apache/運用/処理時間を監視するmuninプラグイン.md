# 処理時間を監視するmuninプラグイン

## Apacheのアクセスログで処理時間を記録する
httpd.confを編集する。

```clike
LogFormat "%t %D \"%r\"" exectime
CustomLog "|/usr/local/apache/bin/rotatelogs /var/log/www/exectime_log.%Y%m%d 86400 540" exectime
```

## muninのプラグインを作成する
以下のファイルをmuninのpluginsディレクトリへ設置する。

```clike
#!/bin/sh

do_ () {
    logfile/var/log/www/exectime_log.$(date +%Y%m%d)
    buffer=1000
    command="tail -n $buffer $logfile | awk '{sum=sum+\$3} END {print \"exec_time.value \"(sum/$buffer)/1000000}'"
    eval $command
    exit 0
}

do_config () {
    echo "graph_title Average page execution time"
    echo "graph_vlabel Seconds"
    echo "graph_category apache"
    echo "graph_args --base 1000 -l 0"
    echo "graph_info Average page execution time"

    echo "exec_time.label Execution time"
    echo "exec_time.type GAUGE"
}

case $1 in
    config|'')
        eval do_$1
esac

exit $?
```

## 参考
http://returnfoo.com/2012/03/average-time-taken-to-serve-a-request-graph-in-munin-using-awk-and-apaches-access-logs/
