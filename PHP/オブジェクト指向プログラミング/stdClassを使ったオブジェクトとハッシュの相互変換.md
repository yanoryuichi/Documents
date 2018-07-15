# stdClassを使ったオブジェクトとハッシュの相互変換

## ハッシュからオブジェクトへ

```
$a = (object) array( 'id' => 1 );
```

```
<object #2 of type stdClass> {
  id => 1,
}
```

## オブジェクトからハッシュへ

```
$b = (array) $a;
```

```
array(
  "id" => 1,
)
```

### オブジェクトからハッシュへ変換するとプロパティは残るがメソッドは消える

```
class X {
  var $v = 10;
  function foo() { return 1; }
}
$x = new X;
$y = (array) $x;
```

```
array(
  "v" => 10,
)
```
