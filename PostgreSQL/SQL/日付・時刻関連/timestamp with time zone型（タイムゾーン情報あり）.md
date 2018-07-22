# timestamp with time zone型（タイムゾーン情報あり）

timestamp型 
: タイムゾーン情報なしのタイムスタンプ型

timestamp with time zone型 （別名 timestamptz型）
: タイムゾーン情報ありのタイムスタンプ型

> 注意: 標準SQLでは、単なるtimestampという記述はtimestamp without time zoneと同じであることを要求します。 PostgreSQLはこれに準じます。 timestamp with time zoneはtimestamptzと省略することが許容されています。これはPostgreSQL独自の拡張です。

### 参考
https://www.postgresql.jp/document/9.4/html/datatype-datetime.html
