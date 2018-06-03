# end()

```clike
<!DOCTYPE html>
<html>
<script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<script>
$(function(){
    var $li = $('<li><span /></li>');
    $li
    .find('span')
      .html('HELLO')
    .end()
    .appendTo('#ul');
});
</script>
<body>
<ul id="ul">
</ul>
</body>
</html>
```

### 説明
以下のようにするとspanがulの直下にappendTo()される（liは消える）。よって、上のようにend()を指定する事でfind()で選択されたspanを解除してからappendTo()する。

```clike
    $li
    .find('span')
      .html('HELLO')
    .appendTo('#ul');
```
