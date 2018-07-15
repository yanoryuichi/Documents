# uオプションで未定義変数の捕捉

例えば以下のようにvarを未定義で（初期化しないで）参照すると、

```bash
set -u
echo $var
echo done
```

以下のようにecho $varの行でスクリプトが異常終了する。

```bash
test.sh: line 4: var: 展開されていない変数
```

以下のようにすれば、スクリプトは「done」と表示して正常終了する。

```bash
set -u
var=1
echo $var
echo done
```

または

```bash
set +u
echo $var
echo done
```
