# WindowsでKaoriYaのVimを使う

## 目的

- WindowsでKaoriYaのVimを使う。
- 設定ファイル等はDropbox上で管理して、それを参照して使うようにする。

## ダウンロード・設置

- http://www.kaoriya.net/からzipファイルをダウンロードする。
- zipファイルを展開し、適当な場所に設置する。
  - 今回は C:\Users\taro\App\Vim に設置する。

## Kaoriya Vimの設定ファイルを読み込まないように調整

- Vimフォルダにvimrc_local.vimファイルとgvimrc_local.vimファイルを作り、以下のように記述する。

### vimrc_local.vim

```clike
let g:vimrc_local_finish = 1
```

### gvimrc_local.vim

```clike
let g:gvimrc_local_finish = 1
```

## 独自の設定ファイルを設置

- コマンドプロンプトを管理者権限で起動する。
- 以下のように、VimフォルダにDropboxにあるVim設定ファイルへのシムリンクを作成する。

```clike
mklink _vimrc "C:\Users\taro\Dropbox\vim\.vimrc"
mklink _gvimrc "C:\Users\taro\Dropbox\vim\.gvimrc"
mklink /D vimfiles "C:\Users\taro\Dropbox\vim\.vim"
```

## 各種vimrcファイルの読み込み順

```clike
:version
```

で確認する。

## 参考
http://d.hatena.ne.jp/teppeis/20080705/1215262928
