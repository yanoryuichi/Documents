# git config

## （git diff等で）画面出力を色つきにする（しない）

```bash
git config --global color.ui auto
git config --global color.ui ''
```

## ページャーを指定する

```bash
git config --global core.pager 'lv -c'
```

### ページャーを使わないなら

```bash
git config --global core.pager cat
```

## エイリアス

```bash
git config --global alias.st status
```

git stでgit statusになる。
