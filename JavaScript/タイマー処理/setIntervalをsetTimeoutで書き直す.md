# setIntervalをsetTimeoutで書き直す

### setInterval()

```clike
var i = 1;
setInterval(function() {
  console.log(i);
  i++;
}, 1000);
```

### setTimeoout()

```clike
var i = 1;
function f1() {
  console.log(i);
  i++;
  setTimeout(f1,1000);
};
f1();
```

### 解説

- 前者のコードのsetInterval()の実行する関数の中で1000ミリ秒以上かかる処理が発生すると、setInterval()は処理を重複しつつ関数を実行してしまう。
- このような問題を避けるためには、後者のコードのようにsetTimeout()を使う。
