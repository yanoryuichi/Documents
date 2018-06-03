# 複数のバージョンのjQueryを共存させる


```clike
<script src="jquery-1.9.1.js"></script>
<script src="jquery-1.6.2.js"></script>

var jq162.jQuery.noConflict(true);
console.log("#1: " + $.fn.jquery);      // 1.9.1
console.log("#2: " + jq162.fn.jquery);  // 1.6.2
```

## 参考
http://api.jquery.com/jQuery.noConflict/
