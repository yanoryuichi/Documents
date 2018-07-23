# Hello World

Vimを起動して、適当なファイルを新規作成する。

```clike
:e test.vim
```

Vimスクリプトを記述する。

```clike
function! MyTest()
   echo "Hello Wolrd"
endfunction
```

Vimスクリプトを読み込む。

```clike
:source %
```

Vimスクリプトを実行する。

```clike
:call MyTest()
```

## 参考
http://nanasi.jp/code/basic.html
