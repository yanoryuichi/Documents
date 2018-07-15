# Factory Methodパターン

```php
<?php
class Foo {
    private $v1 = null;
    private function __construct($options) {
        $v1 = $options['v1'];
    }
    public static function getInstance($options) {
        return new Foo($options);
    }
}
```

## ダメ

```php
$obj = new Foo(array('v1' => 100));
```

```php
PHP Fatal error:  Call to private Foo::__construct() from invalid context in /home/taro/tmp/1.php on line 12
```

## OK

```php
$obj =  Foo::getInstance(array('v1' => 100));
```

```php
object(Foo)#1 (1) {
 ["v1":"Foo":private]=>
 NULL
}
```
