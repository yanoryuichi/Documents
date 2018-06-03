# onclickで割り当てるハンドラ関数に引数を渡す

## 引数無しのハンドラ関数割り当て

```clike
document.getElementById('foo').onclick = func;
```

## 引数有りのハンドラ関数割り当て1
目的の関数を無名関数で包んで割り当てる。

```clike
document.getElementById('foo').onclick = function () { func('hello'); };
```

## 引数有りのハンドラ関数割り当て2

変数を引数にしたい場合、以下のようにしても、ハンドラ関数が実行される（foo0がonclickされる）際にその変数（n）が評価されるので、nはfoo0が期待するような値として得られない。

```clike
for ( var n = 0; n < 3; n++ ) {
 document.getElementById('foo' + n).onclick = function () { func(n); };
}
```

従って、以下のようにハンドラ関数をさらに無名関数で包んで割り当てる、すなわちクロージャにする。nはイベントに割り当てられた時点で評価され、numはその値を得る事が出来る。

```clike
for ( var n = 0; n < 3; n++ ) {
  document.getElementById('foo' + n ).onclick = (function (num) { return func(num) }; })(n);
}
```
