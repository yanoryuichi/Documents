# sleep

## ビジーウェイト

```clike
function sleep(time) {
  var d1 = new Date().getTime();
  var d2 = new Date().getTime();
  while (d2 < d1 + time) {
    d2 = new Date().getTime();
   }
   return;
}
alert("1");
sleep(3000);
alert("2");
```

## setTimeout()

```clike
function sleep(time, callback){
  setTimeout(callback, time);
}
alert("1");
sleep(3000, function (){ alert("2"); } );
```

## jQuery

```clike
 alert("1");
 $(this).delay(1000).queue(function() {
    alert("2");
   $(this).dequeue();
 });
```
