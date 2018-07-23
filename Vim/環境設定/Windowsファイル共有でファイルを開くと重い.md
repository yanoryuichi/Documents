# Windowsファイル共有でファイルを開くと重い

## 現象
Windowsでファイル共有しているファイルをVimで開くと重い。カーソルの移動でスタックしたりする。

## 解決方法1 （多分解決しない）
スワップファイル等を共有先のフォルダに作らないようにしてみる。

```clike
set nobackup
set noswapfile
```

### 参考
WindowsのVim/GVimでネットワーク上のファイル編集や読み込みが遅い場合 ： https://sites.google.com/site/fudist/Home/vim-nihongo-ban/windows-network-edit

## 解決方法2 （多少マシになる）

- 参考で紹介しているページにあるようにプロセスモニターを使うと分かるが、gvimは常に編集しているファイルのファイルパスに含まれる各階層のフォルダを開いたり閉じたりしている。
- これが原因で非常に重くなる。
- （正確には、重くなるのはVimのカレントディレクトリがファイル共有先のフォルダにある場合で、カレントディレクトリがローカルドライブ上なら重くならない。）
- よって、ファイル共有のフォルダ階層を浅くすれば多少マシになる。
- すなわち、\\winserve1\foo\bar\baz\test.txt というファイルを編集すると重いので、\\winserver1\foobar\test.txt というファイルで編集出来るようにする。
- なので、ファイル共有しているフォルダの構成をそもそも変えてしまうか、アクセスしたいフォルダのジャンクションをファイル共有フォルダ直下に作るかして、フォルダ階層を浅くする。

### ジャンクションを作る

```clike
mklink /J foobar foo\bar\baz
```

### 参考

- GVim runs very slowly when editing files on a windows share : http://stackoverflow.com/questions/2103968/gvim-runs-very-slowly-when-editing-files-on-a-windows-share
- slow samba+vim, I'm out of suggestions ... : https://groups.google.com/forum/#!topic/vim_use/peGZozd5JVY
