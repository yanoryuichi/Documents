# hg remove - ファイル削除

```clike
hg remove foo.txt
```

### 登録除外するだけなら hg forget を使う

```clike
hg forget foo.txt
```

上のコマンドではfoo.txtはファイルシステム上では削除されず、Mercurial管理上でのみ登録除外される。

## 参考
http://mercurial-users.jp/manual/hg.1.html#remove
