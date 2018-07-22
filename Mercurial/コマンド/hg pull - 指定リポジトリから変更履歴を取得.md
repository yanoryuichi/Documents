# hg pull - 指定リポジトリから変更履歴を取得

## デフォルトのpull元リポジトリを設定

```clike
[paths]
default      = ssh://hg@bitbucket.org/foo/bar
# default-push = ssh://hg@bitbucket.org/foo/bar
```

hg pullはdefaultで指定する。hg pushはdefault-pushで指定する。

## 参考
http://mercurial-users.jp/manual/hg.1.html#pull
