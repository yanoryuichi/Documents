# SELECTタグ

## 値を取得

```clike
var value = $('#select1').val();
// または
var value = $('#select1 option:selected').val();
```

## 値を設定

```clike
$('#select1').val('ABC');
```

## 選択されたOPTIONタグを取得

```clike
var option = $('#select1 otpion:selected');
```

## 全てのOPTIONタグを取得

```clike
var opts = [];
$('#select1 option').each(function(){
    opts.push($(this));
});
```

## selectedIndexを取得（設定）する

```clike
var num = $('#select1').prop('selectedIndex');
$('#select1').prop('selectedIndex', 0);
```

attr()よりもprop()を使った方が良い。
### 参考
http://www.jquerystudy.info/reference/attributes/prop.html
