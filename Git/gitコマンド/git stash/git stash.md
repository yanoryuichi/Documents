# git stash


## 変更の一覧

```bash
git stash list

stash@{0}: WIP on master: 049d078 added the index file
stash@{1}: WIP on master: c264051 Revert "added file_size"
stash@{2}: WIP on master: 21d80a5 added number to log
```

### 変更の一覧 パッチ付き

```bash
git stash -p
```

## 変更を隠す

```bash
git stash save
git stash #上と同じ。saveは省略できる。
git stash save "Hello, World" #メッセージ付き
```

- メッセージ付きでsaveすると、git stash listすると stash@{0}: On master: Hello, World のようになる。

## 隠した変更を削除する

```bash
git stash drop
git stash drop stash@{2} #どの変更か指定する。指定しなければ直近の変更が適用される。
```

### 隠した変更をすべて削除する

```bash
git stash clear
```

## 隠した変更を復元する

```bash
git stash apply
git stash apply stash@{2} #どの変更か指定する。指定しなければ直近の変更が適用される。
```

### 隠した変更を復元し、削除する

```bash
git stash pop
```

- git applyとgit dropを同時に行う。

## 参考

- https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E3%81%95%E3%81%BE%E3%81%96%E3%81%BE%E3%81%AA%E3%83%84%E3%83%BC%E3%83%AB-%E4%BD%9C%E6%A5%AD%E3%81%AE%E9%9A%A0%E3%81%97%E3%81%8B%E3%81%9F%E3%81%A8%E6%B6%88%E3%81%97%E3%81%8B%E3%81%9F#_git_stashing
- https://git-scm.com/docs/git-stash
- http://www.backlog.jp/git-guide/reference/stash.html
