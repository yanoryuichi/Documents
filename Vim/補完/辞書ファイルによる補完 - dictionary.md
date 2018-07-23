# 辞書ファイルによる補完 - dictionary

## 辞書ファイルのパスの指定

```clike
set dictionary = $VIM/vimfiles/dict/my.dict
```

### 複数の辞書ファイルのパスの指定

```clike
let $MYDICT1 = $HOME . '.vim/dict/my1.dict'
let $MYDICT2 = $HOME . '.vim/dict/my2.dict'

function! SetDict()
  let files = [expand($MYDICT1), expand($MYDICT2)]  
  let &dict = join(files, ',')
endfunction

call SetDict()
```

## 辞書ファイルの中身

```clike
apple
banana
orange
lemon
melon
grape
```

- 1行に1単語を記述する。

## 参考

- http://nanasi.jp/articles/howto/config/dictionary.html
