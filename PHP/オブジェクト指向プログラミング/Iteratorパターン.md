# Iteratorパターン

```php
class MyIterator {
   $pos  = 0;
   $keys = array();
   $vals = array();
   public function __construct($list) {
       $this->keys = array_keys($list);
       $this->vals = array_values($list);
   }
   public function hasNext() {
       return array_key_exists($this->pos + 1, $this->keys);
   }
   public function next() {
       if ($this->hasNext()) {
           $val = $this->vals[$this->pos];
           $this->pos += 1;
           return $val;
       }
   }
   public function rewind() {
       $this->pos = 0;
   }
   public function getArray() {
       return array_combine($this->keys, $this->vals);
   }
} 
```

```php
class Foo {
    public function getIterator() {
        return new MyIetrator($this->array)
    }
}
```

```php
$it = $foo->getIterator();
while ($val = $it->next()) {
}
```
