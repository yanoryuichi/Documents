# pathogenでロードしないモジュールを指定する

- 以下のようにbundleディレクトリにvim-fooというモジュールがあるとする。

```clike
$VIMFILES/bundle/vim-foo
```

- これを読み込まないようにするには.vimrcを以下のようにして、g:pathogen_disabledにモジュール名を追加する。

```clike
let g:pathogen_disabled = []

if v:version < '703'
  call add(g:pathogen_disabled, 'vim-foo')
endif

execute pathogen#infect()
```

## 参考
http://stackoverflow.com/questions/4261785/temporarily-disable-some-plugins-using-pathogen-in-vim
