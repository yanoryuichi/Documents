# コマンドラインの出力結果をyankする

```clike
:redir @a | echo expand("%") | redir END
```

で現在編集しているファイル名がyankされるので、

```clike
"ap
```

でペースト出来る。
