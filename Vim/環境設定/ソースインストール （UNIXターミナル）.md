# ソースインストール（UNIX）

## ソースコード

http://www.vim.org/sources.php

### Github

https://github.com/vim/vim

```clike
git clone https://github.com/vim/vim.git
```

## コンパイル

```clike
./configure --enable-multibyte --with-features=huge --disable-gui --without-x --prefix=$HOME/opt/vim
```

### クリップボードを有効にする（+clipboard）

```clike
 ./configure --enable-multibyte --enable-gui --with-x  --with-features=normal --prefix=$HOME/opt/vim
```

http://superuser.com/questions/235505/compiling-vim-with-xterm-clipboard-support

## 参考

- http://qiita.com/b4b4r07/items/f7a4a0461e1fc6f436a4
