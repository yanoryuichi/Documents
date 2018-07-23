# localvimrc

## ディレクトリ階層ごとに.lvimrcファイルを使い分ける

- .vimrc

```clike
let g:localvimrc_reverse = 1
```

- .lvimrc

```clike
call LocalVimRCFinish()
```

- vimrcと.lvimrcを上のようにする。
- localvimrc_reverseによって、ディレクトリ階層を上に遡って.lvimrcを探す。
- call LocalVimRCFinish()によって、.lvimrcを探すのを止める。
- よって、これより上のディレクトリ階層の.lvimrcは探さない。

```clike
/var/www/.svn/
/var/www/.lvimrc
/var/www/html/.lvimrc
/var/www/html/index.html
/var/www/lib/util.php
```

> The LocalVimRCFinish command
> After a call to this function the sourcing of any remaining local vimrc files will be skipped. In combination with the |g:localvimrc_reverse| option it is possible to end the processing of local vimrc files for example at the root of the project by adding the following command to the local vimrc file in the root of the project:
> call LocalVimRCFinish()

## 参考

- http://www.vim.org/scripts/script.php?script_id=441
- https://github.com/embear/vim-localvimrc
