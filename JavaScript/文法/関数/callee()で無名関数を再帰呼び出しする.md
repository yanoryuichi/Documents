# callee()で無名関数を再帰呼び出しする

```clike
var f = function (n) { return n > 0 ? n * arguments.callee(n - 1) : 1 };
f(3); # => 6
```
