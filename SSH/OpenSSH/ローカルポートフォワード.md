# ArrayObjectクラスとArrayIteratorクラス

## ArrayObjectクラスを継承して配列クラスを作る

```php
class MyArrObj extends ArrayObject {
    function __construct($arr) {
        parent::__construct($arr);
    }
    function double() {
        $arr = $this->getArrayCopy();
        return new MyArrObj(array_merge($arr, $arr));
    }
}
```

## 配列の走査
### 配列クラスをイテレータを使って走査する 1

```php
$arrObj = new MyArrObj(array(1,2,3));
$it = $arrObj->getIterator();
while ($it->valid()) {
    $k = $it->key();
    $v = $it->current();
    printf("%s : %s\n", $k, $v);
    $it->next();
}
```

### 配列クラスをイテレータを使って走査する 2

```php
$arrObj = new MyArrObj(array(1,2,3));
$it = $arrObj->getIterator();
foreach ($it as $k => $v) {
    printf("%s : %s\n", $k, $v);
}
```

### 配列クラスを配列変数的に走査する

```php
$arrObj = new MyArrObj(array(1,2,3));
foreach ($arrObj as $k => $v) {
    printf("%s : %s\n", $k, $v);
}
```

## 配列クラスにメソッドを使って値を追加する

```php
$arrObj->append('4');
```

## 配列クラスに配列キーワードを使って値を追加する

```php
$arrObj[] = 5;
```

## 配列クラスに定義されたメソッドを使う

```php
$arr2 = $arrObj->double();
```

## ArrayIteratorクラスを継承して配列イテレータークラスを作る

```php
class MyArrIt extends ArrayIterator {
    function isEven() {
        $k = $this->key();
        return $k % 2 === 0 ? true : false;
    }
}
```

## 配列クラスのイテレーターを変更する

```php
$arrObj->setIteratorClass('MyArrIt');
```

## 配列イテレータークラスに定義されたメソッドを使う

```php
$it = $arrObj->getIterator();
foreach ($it as $k => $v) {
    $x = $it->isEven() ? 'O' : 'X';
    printf("%s %s : %s\n", $x, $k, $v);
}
```

## 参考

- http://php.net/manual/ja/class.arrayobject.php
- http://jp.php.net/manual/ja/class.arrayiterator.php
