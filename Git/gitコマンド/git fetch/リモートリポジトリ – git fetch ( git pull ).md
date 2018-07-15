# リモートリポジトリ - git fetch ( git pull )

## リモートリポジトリの変更を取得する

```bash
git fetch origin
```

## リモートも含めたブランチ一覧の表示

```bash
git branch -a
```

## ブランチの切り替え

```bash
git checkout dev-branch1
```

## リモートリポジトリのコミットのログを見る

```bash
git log FETCH_HEAD
```

## リモートリポジトリとローカルのHEADの差分を見る

```bash
git diff HEAD FETCH_HEAD
```

## リモートリポジトリと変更をローカルにマージする

```bash
git merge FETCH_HEAD
```


## リモートリポジトリの変更を取得してローカルにマージする

```bash
git pull
```

git pull は git fetch + git merge。

## リモートブランチへpushする

```bash
git push origin dev-branch1
```

## 参考

- http://cmdnote.net/search?q=tag%3Agit-fetch
- http://pinoki.la.coocan.jp/wiki/?Git%2Fgithub%A4%CE%BB%C8%A4%A4%CA%FD#f598e42a
