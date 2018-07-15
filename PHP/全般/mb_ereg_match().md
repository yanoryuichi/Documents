# mb_ereg_match()

```php
$list = array(
    'かな',
    'カナ',
    '０１２',
    'ＡＢＣ',
    '漢字',
);

mb_regex_encoding("UTF-8");

print "全角かな\n";
foreach ($list as $x) {
    if (mb_ereg_match('^[ぁ-んー]+$', $x)) {
        print "OK: " . $x . "\n";
    } else {
        print "NG: " . $x . "\n";
    }
}

print "全角カナ\n";
foreach ($list as $x) {
    if (mb_ereg_match('^[ァ-ヶー]+$', $x)) {
        print "OK: " . $x . "\n";
    } else {
        print "NG: " . $x . "\n";
    }
}

print "全角数字\n";
foreach ($list as $x) {
    if (mb_ereg_match('^[０-９]+$', $x)) {
        print "OK: " . $x . "\n";
    } else {
        print "NG: " . $x . "\n";
    }
}

print "全角英字\n";
foreach ($list as $x) {
    if (mb_ereg_match('^[Ａ-Ｚａ-ｚ]+$', $x)) {
        print "OK: " . $x . "\n";
    } else {
        print "NG: " . $x . "\n";
    }
}

print "全角漢字\n";
foreach ($list as $x) {
    if (mb_ereg_match('^[亜-腕弌-熙 ]+$', $x)) {
        print "OK: " . $x . "\n";
    } else {
        print "NG: " . $x . "\n";
    }
}
```
