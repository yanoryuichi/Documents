# CSS

## 設定・取得

```clike
$('span').css('fontSize', '16px');
var size = $('span').css('fontSize');
```

## まとめて設定

```clike
$('span').css({
  font-size: "16px",
  color:     "red"
});
```

## CSSクラスの追加・削除

```clike
$('span').addClass('color-red');
$('span').removeClass('font-big');
```

## トグル

```clike
<!DOCTYPE html>
<html>
<script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<style type="text/css">
.highlight { background: yellow; }
</style>
<script>
$(function(){
   $("#div").on("click", function(){
     $(this).toggleClass("highlight");
     });
});
</script>
<body>
<div id="div">HELLO</div>
</body>
</html>
```
