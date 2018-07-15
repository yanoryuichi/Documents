# git remote（リモートリポジトリの操作）

## リモートサーバの表示（originのURLの表示）

```bash
git remote -v
```

## リモートリポジトリの追加

```bash
git remote add shared-repo file:///$HOME/tmp/project1.git
```

## リモートリポジトリの削除

```bash
git remote rm shared-repo
```

## リモートリポジトリのURLの変更

```bash
git remote set-url origin git@bitbucket.org:foo/bar.git
```

ここではoriginのURLを変更。

## リモートリポジトリ参照名の変更

```bash
git remote rename origin ex-origin
```

orginからex-originへ。

## 参考
http://progit.org/book/ja/ch2-10.html
