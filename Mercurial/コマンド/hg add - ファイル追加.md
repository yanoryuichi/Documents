# hg add - ファイル追加

## ファイル追加

```clike
hg add 1.txt
```

## ディレクトリ内のファイルをまとめて追加

```clike
hg add foo/
```

## 拡張子等で指定してファイルをまとめて追加
### -I(--include)オプションで包含指定

```clike
hg add -I "set:*.php" .             # 現在のディレクトリの拡張子.phpのファイルをadd
hg add -I "set:**.php" .            # 現在のディレクトリ以下の拡張子.phpのファイルをadd
```

### -X(--exclude)オプションで除外指定

```clike
hg add -X "set:**.gif,**.jpg" .     # 現在のディレクトリ以下の拡張子.gifと.jpg以外のファイルをadd
```

## .hgignoreファイルで除外指定

```clike
vi .hgignore
```

```clike
syntax: glob
*.jpg
*.gif
```

```clike
hg add foo/
```

## hg addの取り消し

```clike
hg add foo.txt
hg revert foo.txt
```

hg revertを使う。

## 参考

- http://mercurial-users.jp/manual/hg.1.html#add
