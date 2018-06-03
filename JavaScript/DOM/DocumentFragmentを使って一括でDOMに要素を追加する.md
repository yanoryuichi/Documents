# DocumentFragmentを使って一括でDOMに要素を追加する

```clike
var list = document.getElementById("list");
var fragment = document.createDocumentFragment();
for (var i = 0; i < 10; i++) {
    var item = document.createElement("li");
    item.innerHTML = "NO." + (i + 1);
    fragment.appendChild(item);
}
list.appendChild(fragment);
```
