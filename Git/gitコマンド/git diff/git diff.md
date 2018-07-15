# git diff

## ワーキングツリーとINDEXの差分

```bash
git diff
```

## INDEXとHEADの差分

```bash
git diff --cached
```

## ワーキングツリーとHEADの差分

```bash
git diff HEAD
```

## コミット間の差分

```bash
git diff HEAD^..HEAD
```

## ファイル名のみ表示

```bash
git diff --name-only HEAD^ HEAD 
```

## ワーキングツリーとINDEXとHEADについて

ワーキングツリー
: 現在の状態

INDEX
: ワーキングツリーからgit addした状態

HEAD
: 最後にコミットした状態

## ローカルのワーキングツリーとリモートのリポジトリの差分

```bash
git diff FETCH_HEAD
```

## マスター・ブランチ間の差分

```bash
git diff master branch1.0 foo.txt
```

## マスター・ブランチ間のファイル変更点の表示

```bash
git diff --name-status master branch1.0
```

```bash
M       foo.txt
D       bar.txt
```

## 参考

- http://d.hatena.ne.jp/murank/20110320/1300619118
