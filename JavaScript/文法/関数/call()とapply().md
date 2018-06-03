# call()とapply()

## call()

```clike
function func(v) {
  alert( v + this.name );
}
func('hello, ');
```

↑ではthis.nameが参照出来ないが、

```clike
var obj  = { name : 'Taro' };
var func = function (v) { alert( v + this.name ); };
func.call(obj, 'Hello, ');
```

↑のようにcall()を使うと任意のオブジェクト { name : 'taro' } に対して関数 func() を実行できる。この際、オブジェクトには何の変更もない。
これを別の方法で実装すると、

```clike
var obj  = { name : 'Taro' };
obj.func = function (v) { alert( v + this.name ); };
obj.func('Hello. ');
delete obj.func;
```

となる。

## apply()
apply()は第2引数を配列で取り（['Hello, ','Mr.']）、適用される関数には引数を並べて渡す（v1,v2）。

```clike
var obj  = { name : 'Taro' };
var func = function (v1, v2) { alert( v1 + v2 + this.name ); };
func.apply(obj, [ 'Hello, ', 'Mr.' ]);
```

これはcall()でも以下のようにして実装出来る。

```clike
var obj = { name : 'Taro' };
var func = function (v1, v2) { alert( v1 + v2 + this.name ); };
func.call( obj, 'Hello, ','Mr.' );
```

引数は省略して、argumentsを利用しても良い。

```clike
var obj    = { name : 'Taro' };
var func   = function () { alert( arguments[0] + arguments[1] + this.name ); };
var caller = function () { func.apply( obj, arguments ) };
caller( 'Hello, ','Mr.' );
```
