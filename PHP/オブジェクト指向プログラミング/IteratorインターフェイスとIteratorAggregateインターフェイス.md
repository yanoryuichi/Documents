# IteratorインターフェイスとIteratorAggregateインターフェイス

```php
class MyArray implements IteratorAggregate {
    private $array = array();

    public function __construct($array) {
        $this->array = $array;
    }

    public function getIterator() {
        #return new ArrayIterator($this->array);
        return new MyIterator($this->array);
    }
}

class MyIterator implements Iterator {
    private $position = 0;

    public function __construct($array) {
        $this->array = $array;
        $this->position = 0;
    }

    function rewind() {
        $this->position = 0;
    }

    function current() {
        return "VAL: " . $this->array[$this->position];
    }

    function key() {
        return "KEY: " . $this->position;
    }

    function next() {
        ++$this->position;
    }

    function valid() {
        return isset($this->array[$this->position]);
    }

    function getPos() {
        return $this->position;
    }

    function size() {
        return sizeof($this->array);
    }

    function isEven() {
        return $this->position % 2 == 0 ? true : false;
    }
}

$arrayObj = new MyArray(array(100,200,300));
foreach ($arrayObj as $k => $v) {
    print "$k $v\n";
}
$it = $arrayObj->getIterator();
print $it->size() . "\n";
foreach ($it as $k => $v) {
    print ($it->isEven() ? 'O' : 'X') . " $k $v\n";
}
$it = new MyIterator(array(100,200,300));
print $it->size() . "\n";
foreach ($it as $k => $v) {
    print $it->getPos() . ": $k $v\n";
}
```

```
KEY: 0 VAL: 100
KEY: 1 VAL: 200
KEY: 2 VAL: 300

3
O KEY: 0 VAL: 100
X KEY: 1 VAL: 200
O KEY: 2 VAL: 300

3
0: KEY: 0 VAL: 100
1: KEY: 1 VAL: 200
2: KEY: 2 VAL: 300
```

Iteratorインターフェイスを実装したイテレータクラスを作る。コレクションクラスに対してIteratorAggregateインターフェイスを割り当て、getIterator()を実装する際にそのイテレータークラスを指定する。

なお、イテレータクラスのメソッド（ここではisEven()やsize()）は、コレクションクラスのインスタンスからは呼び出せず、イテレータークラスのインスタンスを作ってそこから呼び出す。

## 参考

- Iterator インターフェイス http://www.php.net/manual/ja/class.iterator.php
- IteratorAggregate インターフェイス http://www.php.net/manual/ja/class.iteratoraggregate.php
