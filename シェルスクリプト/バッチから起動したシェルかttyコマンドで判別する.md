# バッチから起動したシェルかttyコマンドで判別する


以下のようなシェルスクリプトをcronに登録してバッチ処理として実行すると、結果は"NOT terminal"になる。

```bash
#!/bin/bash

if tty -s; then
    echo "terminal" > /tmp/result.txt
else
    echo "NOT terminal" > /tmp/result.txt
fi
```

## 参考
http://linux.die.net/man/1/tty
