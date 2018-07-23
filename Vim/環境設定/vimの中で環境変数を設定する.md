# vimの中で環境変数を設定する

```clike
:let $PATH .= ";" . expand('C:\foo\bin')
```

これでvimの中で外部コマンドを呼び出す際に環境変数$PATHの中に"C:\foo\bin"が含まれることになる。

### 参考

https://vi.stackexchange.com/questions/2076/whats-the-difference-between-let-and-set
