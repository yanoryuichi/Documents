# hg push - 指定リポジトリへ変更履歴の反映


## デフォルトのpush先リポジトリを設定する

```clike
vi .hg/hgrc
```

```clike
[paths]
default-push = ssh://hg@bitbucket.org/foo/bar
```

## hg push出来るリビジョンがあるか確認する

```clike
hg outgoing
```

```clike
ssh://hg@bitbucket.org/foo/bar と比較中
ssh hg@bitbucket.org 'hg -R foo/bar serve --stdio' の実行中
変更点を探索中
リビジョン:   3:015gg123afff
タグ:         tip
ユーザ:       taro
日付:         Fri Jan 24 11:55:48 2014 +0900
ファイル:     test.txt src/test.php
説明:
修正
```

### 参考
http://mercurial-users.jp/manual/hg.1.html#outgoing

## 参考

- http://mercurial-users.jp/manual/hg.1.html#push
