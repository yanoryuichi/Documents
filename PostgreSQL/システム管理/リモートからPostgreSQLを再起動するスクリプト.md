# リモートからPostgreSQLを再起動するスクリプト

```clike
#!/bin/sh

DB_NAME=my_db
DB_PGDATA=/usr/local/pgsql/data

echo "### Check PostgreSQL is running."
ssh -t -l postgres db.example.com "pg_ctl -D $DB_PGDATA status" | grep 'is running'
if [ $? -ne 0 ]; then
  echo
  echo "### Start PostgreSQL."
  ssh -t -l postgres db.example.com "pg_ctl -w -D $DB_PGDATA start"
else
  echo
  echo "### Restart PostgreSQL
  ssh -t -l postgres db.example.com "pg_ctl -w -D $DB_PGDATA restart"
fi
[[ $? -ne 0 ]] && echo "### Error! Exit." && exit 1
echo
echo "### Done."
```

## 参考

- http://www.postgresql.jp/document/current/html/app-pg-ctl.html
- http://archives.postgresql.org/pgsql-bugs/2008-09/msg00130.php
