# 画像フォルダとファイルをignoreしつつプロジェクトフォルダ以下をimportする

## プロジェクトフォルダ構成

```bash
.
|-- 1.gif
|-- 1.txt
|-- foo
|   |-- 1.txt
|   `-- img
|       `-- 1.jpg
`-- img
```

## 目的
プロジェクトフォルダ以下にある、imgフォルダと拡張子.gif/.jpgはsvn:ignoreして除外しつつ、その他のフォルダやファイルはimportする。

## 手順
### global-ignoresに画像フォルダとファイルを指定

```bash
vi $HOME/.subversion/config
```

```bash
global-ignores = img *.gif *.jpg
```

### importする

```bash
svn import -m 'import project' file:///var/svn/myproject
```

### global-ignoresの解除

```bash
vi $HOME/.subversion/config
```

```bash
#global-ignores = img *.gif *.jpg
```

### プロジェクトフォルダをワーキングコピーにする

```bash
svn co file:///var/svn/myproject . --force
```

### svn:ignoreを設定してコミット

```bash
cat > ignorelist
img
*.gif
*.jpg
svn ps -R svn:ignore -F ignorelist .
svn ci -m 'set svn:ignore'
rm ignorelist
```
