# PhpStorm

## ホームディレクトリをAppDataに変更する

メモ帳等を管理者権限で起動して、PhpStorm.exe.vmoptionsファイル（例 "C:\Program Files (x86)\JetBrains\PhpStorm 5.0.4\bin\PhpStorm.exe.vmoptions"）を開いて、以下のようにuser.homeにAppDataの適当なパスを設定する。

```
-Duser.home=C:\Users\taro\AppData\Roaming\PhpStorm
```

## IdeaVimプラグイン
### インストール
メニュー→Settings→Pluginsを選び、"IdeaVim"で検索して、インストールする。
### 設定
PhpStormで設定した${user.home}（通常は$HOMEまたは%USERPROFILR%）以下の.vimrcまたは_vimrcファイルを読み込むので、そこで設定する。
### vimrcで使える設定
https://github.com/JetBrains/ideavim/blob/master/doc/set-commands.md
### 参考
PhpStorm(WebStorm)でVimキーマップ - http://www.karakaram.com/phpstorm-keymap-vim

## ショートカットキーの参考
http://isann.blog2.fc2.com/blog-entry-304.html
