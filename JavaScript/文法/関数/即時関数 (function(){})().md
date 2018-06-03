# 即時関数 (function(){})()

## 即時関数とは？
「関数定義」「関数呼び出し」を同時に行う。

```clike
(function foo(){ alert(1); })()
```

ここではfooという関数名で定義してるが、無名関数でも良い。

```clike
(function (){ alert(1); })()
```

## 即時関数のメリット

### グローバルスコープを汚さない

```clike
function foo(){ alert(1); }
var foo = 100;
alert(foo); // =>「100」
```

数値のfooが関数のfooを上書きする

```clike
function bar(){ alert(1); }
alert(window.bar);  // =>「function bar(){ alert(1); }」
```

barでグローバルオブジェクトwindowを汚している

```clike
(function baz(){ alert(1); })()
alert(window.baz); // => 「undefined」
```

bazはundefinedで、グローバルを汚されてない

### 即時関数内の変数はスコープが局所化される

```clike
var foo = 1;
(function (){ var foo = 100; alert(foo); })(); // => 「100」
alert(foo); // => 「1」
```

即時関数内のfooは関数内で局所化されており、グローバルスコープのfooと衝突しない。
