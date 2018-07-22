# 画像のdiff

## 概要
TortoiseHgは画像のdiffは表示出来ない。そこで、DiffImgという画像比較ソフトを別に用意して、特定拡張子のファイルはdiff表示にそれを使うようにする。

## DiffImgのインストール

- 下のサイトからダウンロードしてインストールする。
  - http://sourceforge.net/projects/diffimg/
- 今回は"C:\Program Files\TheHive\DiffImg\"にインストールした。

## TortoiseHgの設定
mercurial.iniもしくはリポジトリ内のhgrcに以下のような設定を記述する。

```clike
[extdiff]
cmd.diffimg = C:\Program Files\TheHive\DiffImg\diffimg.exe
opts.diffimg =

[diff-patterns]
**.jpg = diffimg
**.gif = diffimg
**.gif = diffimg
```

### 処理をフックさせたい場合
以下のような内容のファイルをdiffimg.comというファイル名で保存して、上のcmd.diffimgのパスに設定する。

```clike
@echo off
"C:\Program Files\TheHive\DiffImg\diffimg.exe" %1 %2
```
