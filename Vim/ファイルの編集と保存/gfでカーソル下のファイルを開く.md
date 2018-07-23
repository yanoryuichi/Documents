# gfでカーソル下のファイルを開く

## gfでカーソル下のファイルを開く

```clike
include('/home/taro/sample.txt');
```

ファイルパスの上にカーソルを合わせて、

```clike
gf
を実行する。
```

### 新しいタブで開く

```clike
C-W gf
```

### 元のファイルに戻る

```clike
C-^
または
C-o
```

## gfで開くファイル検索パスを変更する (1)

```clike
:set path+=/home/taro
```

でpathを設定し、

```clike
include('sample.txt');
```

sample.txtの上にカーソルを合わせて

```clike
gf
```

を実行すると /home/taro/sample.txt が開く。

## gfで開くファイル検索パスを変更する (2)
Foo_BarクラスであるFoo/Bar.phpファイルが存在するとする。

```clike
:set includeexpr=substitute(substitute(v:fname,'_','/','g'),'$','.php','')
```

として、

```clike
<?php 
$bar = $factory->create('Foo_Bar');
```

でFoo_Barの上にカーソルを合わせてgfを実行するとFoo/Bar.phpが開く。

## gfで開くファイル検索パスを変更する (3)

```clike
:set suffixesadd=.php,.inc
```

## ファイル名と認識する文字列を変更する

```clike
:set isfname-=:
```

とすれば、":"がファイル名として認識されなくなる。Windowsでは"C:\test.txt"のようにドライブレターの区切りに文字に:を使うので含まれている。

### localvimrc.vim

- 上のような特別な設定を.vimrcに書きたくない場合はlocalvimrc.vimを利用する。
- http://www.vim.org/scripts/script.php?script_id=441

### 参考
http://nanasi.jp/articles/howto/file/expand.html#id15
