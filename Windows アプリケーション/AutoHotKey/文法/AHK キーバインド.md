# AHK キーバインド

## *ワイルドカード

```autohotkey
*#c::Run Calc.exe  ; Win+C, Shift+Win+C, Ctrl+Win+C, etc. will all trigger this hotkey.
```

## ~チルダ - アンブロック

```autohotkey
; 以下はaキーを押下すると、abが押下される
; すなわち、元のaの機能がブロックされない
~a::Send, b
```

## $プリフィクス - 無限ループ防止

```autohotkey
; 以下はaキーを押下すると無限にaがsendされる
a::Send, a

; これを避けるため、以下のように先頭に$をつけると、一度だけaがsendされる
$a::Send, a

; なお、以下のようにUseHookをOnにすると、以降すべてのキーバインドが$をつけるのと同等になる
; 基本的にAHKスクリプトの先頭でUseHookをOnにするとよい
#UseHook On
```

- https://www.autohotkey.com/docs/Hotkeys.htm#prefixdollar
- https://www.autohotkey.com/docs/commands/_UseHook.htm
- https://www.autohotkey.com/docs/Hotkeys.htm#Symbols
