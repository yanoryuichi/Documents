# タグファイルをctagsを使わずに作る

## my.tagsファイルを作る

```clike
$bar	C:\SRC\Bar.php	1
$foo	C:\SRC\Foo.php	1
```

ファイルパスは、上のようにフルパスを指定するか、my.tagsファイルから見て相対パスを指定する。

## .vimrcにtagsの設定をする
set tags+=~/my.tags

## タグジャンプしてみる

```clike
<?php
$foo = $bar->getFoo();
```

## 参考
http://superuser.com/questions/94039/how-do-i-create-my-own-tag-files-with-vim-for-interconnected-non-code-text
