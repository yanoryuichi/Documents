# Flyweightパターン

```php
<?php
class Foo {
    private $pool = array();
    public function getValue($key) {
        if (!isset($this->pool[$key])) {
           $this->pool[$key] = $this->create();
        }
        return $this->pool[$key];
    }
    private function create() {
        return rand(0,1000);
    }
    public function clear($key) {
        unset($this->pool[$key]);
    }
}

$f = new Foo;
print $f->getValue(1) . "\n"; # 328
print $f->getValue(1) . "\n"; # 328
print $f->getValue(2) . "\n"; # 912
print $f->getValue(1) . "\n"; # 328
$f->clear(1);
print $f->getValue(1) . "\n"; # 381
```

## キャッシュ処理の実装を独立させて

```php
<?php
class FlyweightImplement {
    public function create() {
        return rand(0,1000);
    }
    public function clear($key) {
        unset($this->pool[$key]);
    }
}
interface FlyweightInterface {
    public function create();
    public function clear($key);
}
class Foo implements FlyweightInterface {
    private $flyweightImplement = null;
    private $pool = array();
    public function __construct() {
        $this->flyweightImplement = new FlyweightImplement;
    }
    public function getValue($key) {
        if (!isset($this->pool[$key])) {
           $this->pool[$key] = $this->create();
        }
        return $this->pool[$key];
    }
    public function create() {
        return $this->flyweightImplement->create();
    }
    public function clear($key) {
        return $this->flyweightImplement->clear($key);
    }
}
```
