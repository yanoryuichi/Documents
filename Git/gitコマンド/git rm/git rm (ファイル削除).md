#git rm (ファイル削除)

## ファイルを削除する

```bash
git rm foo.txt
```

### git rmの取り消し

```bash
 git reset HEAD foo.txt
 git checkout foo.txt
```

間違ってgit rm foo.txtした場合に、foo.txtを復活させる。

## ファイルをINDEXから外す（ファイル自体の削除はしない）

```bash
git --cached foo.txt
```

間違ってgit add foo.txtしてしまい、INDEXから外したい場合に。
