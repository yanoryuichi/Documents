# あるDBのいくつかのテーブルを別のDBのテーブルと入れ替える

## 目的

- あるDBのいくつかのテーブルをダンプする。
- 別のDBの、それらのテーブルをDROPする。
- ダンプしたテーブルを、その別のDBにリストアする。

## スクリプト
標準出力にechoされるので、ファイルに落として、シェルで実行する。

```clike
#!/bin/bash

db_name_from="db_1"
db_name_to="db_2"
tables="user
product
category
order"
function _dump {
    for t in $tables ; do
        echo "pg_dump $db_name_from -t $t > $t.dump"
    done;
}

function _drop {
    for t in $tables ; do
        echo "echo 'DROP TABLE $t' | psql $db_name_to"
    done;
}

function _restore {
    for t in $tables ; do
        echo "psql -f $t.dump $db_name_to"
    done;
}

case "$1" in
    dump)
        _dump;;
    drop)
        _drop;;
    restore)
        _restore;;
    *)
        echo "usage: $0 (dump|drop|restore)"
        exit 1;;
esac
```
