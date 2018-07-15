# git branch （ブランチの操作）

## ブランチの作成

```bash
git branch branch1
```

### カレントブランチの変更

```bash
git checkout branch1
```

### ブランチ作成と共にカレントブランチの変更

```bash
git checkout -b branch1
```

## ブランチの確認

```bash
git branch
```

```bash
* branch1
  master
```

## ブランチの削除
### ローカルブランチの削除

```bash
git branch --delete branch1
git bramch -d branch1
```

### リモートブランチの削除

```bash
git push --delete origin branch1
git push origin :branch1
```

## ブランチ名の変更

```bash
git branch -m branch1 new_branch1
```
