# 全テーブルをGRANTする

```clike
#!/bin/bash
for table in `echo '\dtvs' | psql -t -A -F ',' DB_NAME | cut -f 2 -d ','`
do
   echo "GRANT ALL ON TABLE $table to public;"
   echo "GRANT ALL ON TABLE $table to public;" | psql DB_NAME
done
```

- PostgreSQL8.5からは GRANT ALL ON DB_NAME.* みたいに出来るようになるらしい。
