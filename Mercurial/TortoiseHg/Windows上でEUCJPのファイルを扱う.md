# Windows上でEUCJPのファイルを扱う

## 目的
windows上で文字コードがEUCJPのファイルを扱うと、ワークベンチでファイルの中身を参照したり、変更点の確認をすると
、文字化けしてファイルの中身が表示される。この問題を、TortoiseHgがファイル参照する際にnkfコマンドを介す事で、解決する。

なお、今回はあるリポジトリにあるPHPファイルとHTMLファイルはすべて文字コードがEUCJPであるとして、このリポジトリを扱う為の方法を紹介する。

## 方法
### nkfコマンドのインストール

- 以下よりnkfをダウンロードする。
  - http://www.vector.co.jp/soft/win95/util/se295331.html
- ダウンロードしたZIPファイルを展開して、以下のnkf.exeファイルをコピーする。
  - nkfwin\vc2005\win32(98,Me,NT,2000,XP,Vista,7)ISO-2022-JP\nkf.exe
- nkf.exeファイルをWindowsの実行パスが通ったフォルダーにコピーする。
  - 実行パスの設定には[[ココ>Windows/お気に入りアプリ/ユーティリティ]]で紹介しているRapid Environment Editorを使うと便利。

### TortoiseHgの設定

- リポジトリの設定ファイル.hg/hgrcをテキストエディタで開く。
- 以下のように記述を加える。

```clike
[decode]
**.html = pipe: nkf -S -e
**.php = pipe: nkf -S -e

[encode]
**.html = pipe: nkf -E -s
**.php = pipe: nkf -E -s
```

- decodeで作業領域の取り込みの際にEUCJPへ変換して、encodeで履歴に書き込む際にSJISへ変換する。

## 参考

- http://d.hatena.ne.jp/flying-foozy/20111215/1323944808
- http://cobitech.blogspot.jp/2012/05/jis.html
- http://cobitech.blogspot.jp/2012/05/python.html
