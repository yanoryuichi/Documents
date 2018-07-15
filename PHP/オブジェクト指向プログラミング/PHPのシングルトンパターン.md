# PHPのシングルトンパターン

```php
class Singleton {
    var $num = 0;
    function Singleton($flg=null) {
        if (!$flg){
            die("ERR: use getInstance()\n");
        }
    }

    function &getInstance() {
        static $singleton;
        if ($singleton == null){
            $singleton = new Singleton(true);
        }
        return $singleton;
    }

    function add() {
        $this->num += 1;
    }
}
$s1 =& Singleton::getInstance();
$s2 =& Singleton::getInstance();
$s1->add();
print $s1->num."\n"; // => 1
print $s2->num."\n"; // => 1
$s2->add();
print $s1->num."\n"; // => 2
print $s2->num."\n"; // => 2
```

- getInstance()はリファレンス返しする。function &getInstance()の&が必要ということ。 
- インスタンスもリファレンスとして受ける。$s1 =& xxx の&が必要ということ。
- また、
- new Singleton()は、リファレンス返しでなく、コピーで渡すこと。
- すなわち、$singleton =& new Singleton(true); としてはダメ。
