# map()

## $(SELECTOR).map()

```clike
<input id="name" value="yahoo" />
<input id="url" value="http://www.yahoo.co.jp/" />

var output = $("input").map(function(){
     return $(this).val();
}).get().join(" ");
```

## $.map()

```clike
var people = [
 { name: "taro", age: 10 },
 { name: "jiro", age: 8 }
];
var name_list= $.map(people, function(person){
     return person.name
   });
```

## 参考
http://api.jquery.com/map/
