# Factory+Singletonパターン

```
<?php
class Foo {
    private $time = 0;
    public function __construct() {
        print "creating Foo ..";
        sleep(1);
        print ".. done\n";
        $this->time = @date('H:i:s.u');
    }
    public function getTime() {
        return $this->time;
    }
}

class Factory {
    static private $pool = array();
    private function  __construct() { }
    public static  function create($class) {
        if (!isset(self::$pool[$class])) {
            self::$pool[$class] = new $class;
        }
        return self::$pool[$class];
    }
}

$f0 = new Foo;
$f1 = Factory::create('Foo');
$f2 = Factory::create('Foo');
$f3 = new Foo;
$f4 = Factory::create('Foo');

print $f0->getTime() . "\n";
print $f1->getTime() . "\n";
print $f2->getTime() . "\n";
print $f3->getTime() . "\n";
print $f4->getTime() . "\n";
```


```
creating Foo .... done
creating Foo .... done
creating Foo .... done
17:31:32.000000
17:31:33.000000
17:31:33.000000
17:31:34.000000
17:31:33.000000
```
