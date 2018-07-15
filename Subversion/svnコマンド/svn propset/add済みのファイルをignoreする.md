# add済みのファイルをignoreする

## 目的
今、ワーキングコピーには、

```bash
foo.txt
img/
  1.jpg
  2.png
```

というファイルが存在し、foo.txtとimgはadd済みとする。svn statusすると、

```bash
?       img/1.jpg
?       img/2.png
```

となる。ここから全てのファイルとディレクトリをignoreしたい。

## 方法
### add済みのファイルを（ローカルに保存しつつ）delする

```bash
svn del --keep-local *
```

### ignoreする

```bash
svn ps svn:ignore '*' .
```

### コミットする

```bash
svn ci -m 'ignoreした' .
```
