# HTML Tidyで整形

## HTML Tidyのインストール

- 以下からtidyをインストールする。
  - http://tidy.sourceforge.net/
- どこかパスの通った場所に置く。
  - 今回はtidy.exeをhtml-tidy.exeとリネームして設置した。

## vimrcの設定

- .vim/ftplugin/html.vimに以下のように記述する。

```clike
vmap ,m :!html-tidy -q -i --show-errors 0<CR>
command -range=% -nargs=* Tidy <line1>,<line2>! html-tidy -q -i --show-errors 0<CR>
```

## 参考

- http://vim.wikia.com/wiki/Cleanup_your_HTML
- http://stackoverflow.com/questions/8120291/vim-tidy-makeprg-with-stdin
- http://blog.blueblack.net/item_342
