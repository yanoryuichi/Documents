# DOM関数

### IDから要素を1つ取得 - document.getElementByID(id)

```clike
var elem = document.getElementByID("id");
```

### タグ名から要素リストを取得 - elem.getElementsByTagName(name)

```clike
var inputs = document.getElementsByTagName("input");
for ( var i = 0, n = inputs.length; i < n; i++ ) {
  var input = inputs[i];
  console.log(input.name);
}
```

```clike
var ul = document.getElementById("ul-id");
var li = ul.getElementsByTagName("li")[0];

```

## 要素の属性値を取得・設定

```clike
var name = elem.getAttribute("name"));
```

```clike
elem.setAttribute("href", "http://www.yahoo.co.jp/");
```

### 直下の子ノードリスト - elem.childNodes

```clike
var nodes = document.body.childNodes;
for ( var i = 0, n = nodes.length; i < n; i++ ) {
  console.log(i + ": " + nodes[i]);
}

# <html><body>
# abc
# <div><p>...</p></div>
# xyz
# </body></html>
# 
# 0: [object Text] ( abc )
# 1: [object HTMLDivElement]
# 2: [object Text] ( xyz )
```

### 直下の最初の子ノード - elem.firstChild
childNodes[0]と同じ。

### 要素を作る - document.createElement(name)

```clike
var div = document.createElement("div");
```

### テキストノードを作る - document.createTextNod(text)

```clike
var text = document.createTextNode("abc");
```

### 子ノードの最後にノードを追加する - elem.appendChild(node)

```clike
var div = document.createElement("div");
var t1 = document.createTextNode("this ");
var t2 = document.createTextNode("is ");
var t3 = document.createTextNode("a pen.");
div.appendChild(t1);
div.appendChild(t2);
div.appendChild(t3);
document.body.appendChild(div);
```

### 子ノードの前にノードを追加する - elem.insertBefore(node)

```clike
var li = document.createElement("li");
li.appendChild(document.createTextNode("0"));
var ul = document.getElementsByTagName("ul")[0];
ul.insertBefore(li, ul.firstChild);
```

### ノードをchildNodesから削除する - elem.removeChild(node)

```clike
var ul = document.getElementsByTagName("ul")[0];
var li = ul.getElementsByTagName("li")[0];
ul.removeChild(li);
```

削除されるノードはchildNodesでなければならないので、あるノード内の全てのノードを再帰的に削除する場合、firstChildを使って以下のようにする。

```clike
var div = document.getElementsByTagName("div")[0];
while ( div.firstChild ) div.removeChild(div.firstChild);
```
