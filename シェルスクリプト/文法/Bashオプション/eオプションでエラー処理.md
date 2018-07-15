# eオプションでエラー処理

set -eすると、式が非ゼロな終了コードを返した時点で、スクリプトは勝手にexitする。
例えば、

```bash
set -e
false
if [ "$?" -ne 0 ]; then
   echo error; exit 1;
fi
echo done
```

は、実行すると何も表示せずに終了する。これが下のようにset +eなら、

```bash
set +e
false
if [ "$?" -ne 0 ]; then
    echo error; exit 1;
fi
echo done
```

「error」と表示して終了する。なお、set -eすると$?を使ったエラー処理が出来なくなるので、代わりに下のようにしてエラーを補足する。

```bash
set -e
false || { echo error; exit 1; }
```

```bash
set +e
false || { echo error; exit 1; }
```

上のようにすると、いずれも「error」と表示して終了する。
