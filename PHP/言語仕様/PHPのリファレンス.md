# PHPのリファレンス
##リファレンス返し

```php
$num = 10;
function &func1() {
    global $num;
    return $num;
}
$ref =& func1();
$ref = $ref + 1;
print $num; // => 11
```

- 関数func1()の中で使いたいグローバル変数$numを見つけ、それをリファレンス変数$refに結びつける。
- リファレンス変数を操作することで、グローバル変数の値を変えることできる。

```php
$num = 10;
function &func1() {
    $num = $GLOBALS['num'];
    return $num;
}
$ref =& func1();
$ref = $ref + 1;
print $num; // => 10 注意：11ではない！
```

- func1()が返すのは、リファレンスであること。
- 値を返したら、意味をなさない。

```php
$num = 10;
function &func1() {
    $num =& $GLOBALS['num'];
    return $num;
}
$ref =& func1();
$ref = $ref + 1;
print $num; // => 11
```

$GLOBALSを使う場合、=& で取り出す。

##  関数内でのグローバル変数の参照
[[PHPマニュアル>http://www.php.net/manual/ja/language.references.whatdo.php]]より
>global $var; は、$var =& $GLOBALS['var']; の短縮版だと考えてください。 これにより、他のリファレンスを $var に代入し、 ローカル変数のリファレンスのみを変更します。

```php
function func1($flg) {
    global $g1, $g2;
    if ($flg) {
        $g2 =& $g1;
    } else {
        $GLOBALS['g2'] =& $g1;
    }
}

$g1 = 1;
$g2 = 2;
func1(true);       // globalを使う
print "$g1 $g2\n"; // => 1 2

$g1 = 1;
$g2 = 2;
func1(false);      // $GLOBALS[]を使う
print "$g1 $g2\n"; // => 1 1
```

```php
function func1($flg) {
    global $g1, $g2;
    if ($flg) {
        $g2 = $g1;
    } else {
        $GLOBALS['g2'] = $g1;
    }
}

$g1 = 1;
$g2 = 2;
func1(true);       // globalを使う
print "$g1 $g2\n"; // => 1 1

$g1 = 1;
$g2 = 2;
func1(false);      // $GLOBALS[]を使う
print "$g1 $g2\n"; // => 1 1
```
