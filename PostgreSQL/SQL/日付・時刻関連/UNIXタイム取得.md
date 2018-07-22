# UNIXタイム取得


## EXTRACT(EPOCH FROM TIMESTAMP)の返す結果が9.2から変更された

- EXTRACT(EPOCH FROM TIMESTAMP)の返す結果が9.2から変更された。
- 9.1ではEXTRACT()はタイムゾーン情報なしのタイムスタンプ型を前提にしている。
- 9.2ではタイムゾーン情報ありのタイムスタンプ型を考慮している。
- 9.2でタイムゾーン情報なしのタイムスタンプ型を引数に渡すと、ローカルタイム（つまりタイムゾーン情報がある）のUNIXタイムが返る。
- 使い方次第だが、Perlのtime()やPHPのtime()はUTCのUNIXタイムを期待している。
- なお、以下のtimestamp型はタイムゾーン情報なしのタイムスタンプ型のこと。timestamp with time zone型またはtimestamptz型がタイムゾーン情報ありのタイムスタンプ型のこと。

### PostgreSQL 9.1

> date型とtimestamp型の値において、1970-01-01 00:00:00 UTCからの秒数（負の数の場合もあり）。interval型の値ではその時間間隔における秒の合計。

https://www.postgresql.jp/document/9.1/html/functions-datetime.html


### PostgreSQL 9.2

> timestamp with time zone型の値において、1970-01-01 00:00:00 UTCからの秒数（負の数の場合もあり）。dateとtimestamp型の値において、ローカルタイムの1970-01-01 00:00:00からの秒数。interval型の値ではその時間間隔における秒の合計。

https://www.postgresql.jp/document/9.2/html/functions-datetime.html


## PostgreSQL 9.2以降でEXTRACT(EPOCH FROM TIMESTAMP)でUTCのUNIXタイムを取得する

```clike
SELECT EXTRACT(EPOCH FROM col1::timestamp with time zone) FROM t1;
```


## 参考

- https://stackoverflow.com/questions/27830790/postgresql-9-3-5-difference-from-8-3-6-when-extracting-epoch-from-casted-value
- https://stackoverflow.com/questions/29536542/different-results-for-extract-epoch-on-different-postgresql-servers
- https://dba.stackexchange.com/questions/2796/how-do-i-get-the-current-unix-timestamp-from-postgresql
- http://php.net/manual/ja/function.time.php
- http://perldoc.jp/func/time
