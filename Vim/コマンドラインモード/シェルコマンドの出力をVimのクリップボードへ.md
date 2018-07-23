# シェルコマンドの出力をVimのクリップボードへ

## lsの結果をクリップボードへ

```clike
:redir @*
:silent ls
:redir END
```
