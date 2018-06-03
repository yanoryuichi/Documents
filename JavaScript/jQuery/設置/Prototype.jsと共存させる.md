# jQueryをPrototype.jsと共存させる


```clike
<script src="prototype.js"></script>
<script src="jquery.js"></script>
<script type="text/javascript">
$.noConflict();
jQuery(document).ready(function ($) {
});
// もしくは
(function ($) {
})(jQuery);
</script>
```

- 最初に$.noConflict()で$をPrototypeに戻す。
- 次にjQuery.read()あるいは即時実行関数を使って$をjQueryにする。
