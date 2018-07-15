# ADODB
## 前提

```
 Column |            Type             | Modifiers 
--------+-----------------------------+-----------
 n      | integer                     | 
 s      | text                        | 
 d      | timestamp without time zone | 
```

##接続

```php
include('lib/adodb.inc.php');
$dsn = 'postgres://user_name:pass@localhost/db_name';
$dsn = 'mysql://user_name:pass@localhost/db_name';
$conn = &ADONewConnection($dsn);
$conn->Close(); # 任意
```

##SELECT

###省略形を使ったSELECT

```php
$col = $conn->GetOne('select * from t1');                // 1行目の1カラム目だけ
if (!$col){
    print $conn->ErrorMsg();
}
$row = $conn->GetRow('select * from t1');                // 1行目だけ
$stmt = $conn->Prepare('select * from t1 where n = ?');  // 全行
$all = $conn->GetAll($stmt,array(1));
```

GetRow()とGetAll()の返値は以下のように数値インデックスとカラム名インデックスの複合。

```php
Array
(
   [0] => 1
   [n] => 1
   [1] => test
   [s] => test
   [2] => 2006-05-01
   [d] => 2006-05-01
)
```

###カーソル（ポインタ）を使ったSELECT

```php
$conn->SetFetchMode(ADODB_FETCH_ASSOC);
$rs =& $conn->execute('select * from t1');
if (!$rs){
    print $conn->ErrorMsg(); exit;
}  
while (!$rs->EOF){
    print_r($rs->fields);
    $rs->MoveNext();
}
```

###カーソルの移動

```php
$rs->Move($to);   # $toは0から始る
$rs->MoveFirst(); # Move(0)と同じ
$rs->MoveLast();  # Move(RecordCount()-1)と同じ
```

###全行取得
現在のカーソル位置から最後の行まで（$number_of_rowsがあればそれだけ）取得。

```php
$rs->GetArray(); $rs->GetAssoc($number_of_rows);
```

###レコード件数

```php
$rs->RecordCount();
```

###取得したレコード配列の構造の指定
接続($conn)が複数個ある場合は、SetFetchMode()を使う。

```php
$ADODB_FETCH_MODE = ADODB_FETCH_NUM;    # 配列
$conn->SetFetchMode(ADODB_FETCH_ASSOC); # 連想配列
```

##INSERT/UPDATE

```php
$s = $conn->qstr("isn't");
$d = $conn->DBDate(time());
$d = $conn->DBDate('2006-02-02 10:15:00');
$sql = "insert into t1 (n,s,d) values (1,$s,$d) ";
if ($conn->Execute($sql) === false) {
    print $conn->ErrorMsg();
}
```

###AutoExecute()

```php
$data['s'] = 'test'; $data['n'] = 10; $data['d'] = time();
$conn->AutoExecute('t1', $data, 'INSERT');
```

```php
$data['n'] = 10; $data['d'] = '2006-03-03';
$conn->AutoExecute('t1', $data, 'UPDATE','n = 1'); 
$num = $conn->Affected_Rows(); # 影響されたレコード数 
```

###シリアル型（オートインクリメント）IDの取得

```php
$conn->Execute($sql);
$id = $conn->Insert_ID();
```

###NULLのインサート
以下のように指定する。

```php
$ADODB_FORCE_TYPE = ADODB_FORCE_IGNORE;
$ADODB_FORCE_TYPE = ADODB_FORCE_NULL;
$ADODB_FORCE_TYPE = ADODB_FORCE_EMPTY;
$ADODB_FORCE_TYPE = ADODB_FORCE_VALUE; # デフォルト
```

```php
$data['n'] = null; $data['s'] = ''; $data['d'] = false;
$conn->AutoExecute('t1', $data, 'INSERT');
```

を実行すると、上から、


```php
=> 実行されない
=> INSERT INTO t1 ( N, S, D ) VALUES ( null, null, null )
=> INSERT INTO t1 ( N, S, D ) VALUES ( 0, '', null )
=> INSERT INTO t1 ( N, S, D ) VALUES ( null, '', null )
```

## プリペアドステートメント

```php
$sql = "INSERT INTO t1 (n,s,d) VALUES (?,?,?)";
$stmt = $conn->Prepare($sql);
$tmp = array('"AA','BB\'','C\C');
for ($i=0;$i<3;$i++){
    $conn->Execute($stmt,array($i,$tmp[mt_rand(0,2)],$conn->DBDate(time())));
}
```

##文字列エスケープ

```php
$d = $conn->DBDate('2006-05-09');          # => '2006-05-09'
$d = $conn->DBDate('2006-05-09 10:30:20'); # => '2006-05-09 10:30:20'
$d = $conn->DBDate(time());                # => '2006-05-09'
$d = $conn->DBDate('');                    # => null
$t = $conn->DBTimeStamp('2006-05-09');     # => '2006-05-09'
$t = $conn->DBTimeStamp(time());           # => '2006-05-09 10:30:20'
$t = $conn->DBTimeStamp(false);            # => null
$s = $conn->qstr('"');                     # => mysql:'\"' postgres:'"'
$s = $conn->Quote("\"");                   # same as qstr()
```

## 参考
http://www.souken.co.jp/tech/php/adodb/docs-adodb-ja.htm
