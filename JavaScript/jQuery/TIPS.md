# jQuery TIPS

## ターゲット要素にアクセスするには$(this)を使う

```clike
$("#btn").click(function(){
 $("#btn").addClass("highlight");
});
```

↓

```clike
$("#btn").click(function(){
 $(this).addClass("highlight");
});
```
