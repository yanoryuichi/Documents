# プリペアドステートメントのSQLを組み立てる

- カラム名をキーにしたハッシュを元にプリペアドステートメント用のSQLを作る。
- array_join()の使い方など若干不自然な部分もあるが、PHPには無名関数がなくarray_mapが使い物にならないので仕方ない。

```php
<?
// 以下のようなハッシュを想定する
$req = array('user_id' => 100, 'name' => 'taro', 'age' => 20, 'tel' => '090-0000-0000');

// 元になるハッシュから必要な値だけ取り出す
$data = array();
foreach (array('user_id','name','age','tel') as $n) {
    $data[$n] = $req[$n];
}

// インサート文
$sql = sprintf('insert into user (%s) values (%s)',
    join(', ',array_keys($data)),
    join(', ',array_pad(array(),sizeof($data),'?'))
);
print "$sql\n";

// アップデート文
$user_id = $data['user_id'];
unset($data['user_id']);    // user_idはwhere句で使い、ここでは不要
$sql = sprintf('update user set %s =? where user_id = ?',
    join(' = ?, ',array_keys($data)),
    $user_id
);
print "$sql\n";
?>
```
