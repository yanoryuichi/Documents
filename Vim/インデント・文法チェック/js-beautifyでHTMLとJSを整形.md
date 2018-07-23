# Nodeのjs-beautifyで整形

## js-beautifyのインストール

### Node.jsのインストール

- http://nodejs.org/download/

### js-beautifyのインストール

```clike
npm -g install js-beautify
```

https://github.com/beautify-web/js-beautify

### インストールされるコマンド

- js-beautify
- html-beautify
- css-beautify

## Vimのjs-beautifyプラグインをインストール

- ZIPファイルをダウンロードするか、git cloneして、VIMプラグインディレクトリに設置する。
- https://github.com/maksimr/vim-jsbeautify

## .vimrc設定

```clike
if executable('js-beautify')
  command! -range=% -nargs=* HTMLTidy <line1>,<line2>call RangeHtmlBeautify()
  command! -range=% -nargs=* JSTidy <line1>,<line2>call RangeJsBeautify()
  command! -range=% -nargs=* CSSTidy <line1>,<line2>call RangeCSSBeautify()
  command! -range=% -nargs=* JSONTidy <line1>,<line2>call RangeJsonBeautify()
endif
```
