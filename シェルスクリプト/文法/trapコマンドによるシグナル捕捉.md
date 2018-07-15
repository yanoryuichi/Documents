# trapコマンドによるシグナル捕捉

## シグナル捕捉をしないスクリプト

何か重い処理を行うスクリプトがあったとして、スクリプトが重複して実行される事を防ぐためにロックファイルを使って処理を制御する。以下がその例のスクリプト。

```bash
#!/bin/bash

lockfile=/tmp/lockfile

if [ ! -e $lockfile ]; then
    touch $lockfile
    echo "Do somethnig."
    sleep 5
    echo "Done."
    rm $lockfile
else
    echo "The process is already running."
fi
```

このスクリプトは実行中に異常終了するとロックファイルが残ってしまい、再度実行しても正常に機能しなくなってしまう。


## シグナル捕捉するスクリプト

上のような事態を防ぐためにtrapコマンドを使って、ロックファイルを削除する処理を盛り込んだのが、以下の例。

```bash
#!/bin/bash

lockfile=/tmp/lockfile

if [ ! -e $lockfile ]; then
    trap "echo Trapped; rm -f $lockfile; exit" INT QUIT TERM
    touch $lockfile
    echo "Do somethnig."
    sleep 5
    echo "Done."
    rm $lockfile
else
    echo "The process is already running."
fi
```

このスクリプトを実行中にkillコマンドでプロセスを殺したり、CTRL+C押下でプロセスを中断したとしても、trapコマンドで指定した"echo Trapped; rm -f $lockfile; exit"が実行されるので、ロックファイルは削除される。

### 終了時に必ずある処理を行うようにする

trapコマンドにはいろいろなシグナルを指定できるが、EXITを指定する事でプロセス終了時に必ずある処理を行うように出来る。下がその例。

```bash
#!/bin/bash

cleanup() {
    rm -f $lockfile
    echo Done.
    exit
} 

lockfile=/tmp/lockfile

if [ ! -e $lockfile ]; then
    trap cleanup EXIT
    touch $lockfile
    echo "Do somethnig."
    sleep 5
else
    echo "The process is already running."
fi
```

## 使用可能なシグナル

```bash
kill -l
```

ちなみにKILL(kill -KILLに)シグナルは捕捉できない。
