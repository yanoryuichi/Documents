# 環境変数VIM VIMRUNTIME

## 環境変数VIM/VIMRUNTIME

- Vimの実行で参照されるディレクトリパス。
- OSの環境変数として指定する。（通常はvimrcなどの設定ファイルの中では指定しない。）
- 普通にVimを使うだけなら指定しなくてもよい。読み込むプラグインやvimrcファイルのパスを変えたい場合などは指定する。

## VIM

- 設定ファイル .vimrc/_vimrc等を置く。
- .vimrc等の読み込み状況は:versionで確認出来る。
  - Linuxの例 /usr/share/vim
  - Windowsの例 C:\(Vimを設置したディレクトリ) ※下にgvim.exeがある

## VIMRUNTIME

- Vimに必要な多くのファイル（プラグインファイル、ヘルプファイル、カラースキームファイルなど）を置くディレクトリ。
  - Linuxの例 /usr/share/vim/vim74
  - Windowsの例 C:\(Vimを設置したディレクトリ)\vim80
- 参考 http://vim.wikia.com/wiki/Understanding_VIMRUNTIME

```clike
/usr/share/vim/vim74/
├── autoload
├── bugreport.vim
├── colors
├── compiler
├── delmenu.vim
├── doc
├── evim.vim
├── filetype.vim
├── ftoff.vim
├── ftplugin
├── ftplugin.vim
├── ftplugof.vim
├── gvimrc_example.vim
├── indent
├── indent.vim
├── indoff.vim
├── keymap
├── lang
├── macros
├── menu.vim
├── mswin.vim
├── optwin.vim
├── plugin
├── print
├── scripts.vim
├── spell
├── synmenu.vim
├── syntax
├── tutor
└── vimrc_example.vim
```


## vimrcファイルの検索パスの確認

- :version で確認できる。
- ユーザーvimrcファイルは最初に見つかったものを読み込み、以降は読み込まない。

### Linuxの例

```clike
  system vimrc file: "/etc/vimrc"
    user vimrc file: "$HOME/.vimrc"
2nd user vimrc file: "~/.vim/vimrc"
     user exrc file: "$HOME/.exrc"
 fall-back for $VIM: "/etc"
f-b for $VIMRUNTIME: "/usr/share/vim/vim74"
```

### Windowsの例

```clike
   system vimrc file: "$VIM\vimrc"
     user vimrc file: "$HOME\_vimrc"
 2nd user vimrc file: "$HOME\vimfiles\vimrc"
 3rd user vimrc file: "$VIM\_vimrc"
      user exrc file: "$HOME\_exrc"
  2nd user exrc file: "$VIM\_exrc"
  system gvimrc file: "$VIM\gvimrc"
    user gvimrc file: "$HOME\_gvimrc"
2nd user gvimrc file: "$HOME\vimfiles\gvimrc"
3rd user gvimrc file: "$VIM\_gvimrc"
```
