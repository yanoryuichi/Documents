# find()とfileter()

```clike
<!DOCTYPE html>
<html>
<script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<script>
$(function(){
    var $li_list = $("li");
    $li_list.filter(".foo").each(function(){
      console.log($(this).html());
      });
    console.log("---");
    $li_list.find(".foo").each(function(){
      console.log($(this).html());
      });
    console.log("====");

    $li_list = $("#list");
    $li_list.filter(".foo").each(function(){
      console.log($(this).html());
      });
    console.log("---");
    $li_list.find(".foo").each(function(){
      console.log($(this).html());
      });
});
</script>
<body>
<ul id="list">
  <li class="foo">foo1</li>
  <li class="">2</li>
  <ul>
    <li class="foo">foo2-1</li>
  </ul>
  <li class="foo">foo3</li>
</ul>
</body>
</html>
```

### find()

```clike
$("li").find(".foo")
```

liの子孫要素からfooクラスの要素を探す。

### filter()

```clike
$("li").filter(".foo")
```

li要素の内、fooクラスな要素を絞り込む。
