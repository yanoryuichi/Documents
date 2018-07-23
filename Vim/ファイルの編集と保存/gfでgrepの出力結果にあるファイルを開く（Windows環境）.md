# gfでgrepの出力結果にあるファイルを開く（Windows環境）

### 問題

例えば、Windowsでgrepでファイルリストを作り、それをVimで開くと、

```clike
PS tmp> grep "abc" *.txt > list.txt
PS tmp> gvim.exe .\list.txt
```

以下のようになるが、

```clike
./bar.txt:2:abc
./foo.txt:2:abc123
./foo.txt:4:abc
```

ここでbar.txtにカーソルを合わせてgfすると、以下のようなエラーメッセージが表示されて、ファイルを開くことができない。

```clike
E447: pathには "./bar.txt:2:abc" というファイルがありません
```

これはWindowsではisfnameに:が含まれるから、

```clike
:set isfname
isfname=@,48-57,/,\,.,-,_,+,,,#,$,%,{,},[,],:,@-@,!,~,=
```

### 解決方法1 :を適当な文字へ置換する

そこで:を適当な文字（スペースとか）へ置換する。

```clike

```

:%s/:\</ /

すると、以下のようになる。

```clike
./bar.txt 2:abc
./foo.txt 2:abc123
./foo.txt 4:abc
```

これでbar.txtにカーソルを合わせてgfすると、bar.txtが開く。ちなみに、gFすると、ちゃんと2行目が開く。

### 解決方法2 ファイルパス部分をビジュアルセレクトしてgfする

- ファイルパス部分をビジュアルセレクトしてgfする。
- 大量にファイルがある場合は1の方法で、少ない場合は2の方法で。

### 参考

- http://thinca.hatenablog.com/entry/20140324/1395590910
- もっとちゃんとした解決策が必要な場合は、プラグインやファンクションを作ると良いようだ。
