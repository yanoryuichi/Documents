# CSV出力

```php
ob_implicit_flush(true);
header('Content-Disposition: attachment; filename=user.csv.csv');
header('Content-Type: Application/Octet-Stream');
header('Pragma: private');
header('Cache-control: private, must-revalidate');
foreach ($rows as $row) {
    $tmp = array();
    foreach (array('name','age','tel','tel') as $k) {
        $tmp[] = '"' . preg_replace('/"/','""',$row[$k]) . '"';
    }
    print mb_convert_encoding(join(',',$tmp),'SJIS',mb_internal_encoding()) . "\r\n";
}
```

IE7だとHTTPヘッダーでキャッシュコントロールの指定が必要。
