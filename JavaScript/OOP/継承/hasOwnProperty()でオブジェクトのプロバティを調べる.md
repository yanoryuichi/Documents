# hasOwnProperty()でオブジェクトのプロパティを調べる

```clike
Object.prototype.bar = 1; 
var foo = {goo: undefined};

foo.bar;       // => 1
'bar' in foo; // => true

foo.hasOwnProperty('bar'); // => false
foo.hasOwnProperty('goo'); // => true
```

hasOwnPropery()はオブジェクトのprototypeチェーンをたどらない。
