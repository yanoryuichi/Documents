# in演算子

## オブジェクトを定義

```clike
var user = {
  name: "Taro",
  age: 10,
  email: "taro@example.com"
};
```

## in演算子によるイテレーション

```clike
for ( var item in user ) {
    console.log( "DEBUG: " + item + " => " + user[item] );
}
```

## in演算子による真偽判定

```clike
if ("age" in user) {
    console.log("DEBUG: Found!");
}
```
