#xdebug

## 全般

- Xdebug1系と2系があり、得られる内容は同じようなものだが、設定や関数がかなり違う。
- Xdebug2系だと、結果ファイルをWinCacheGrindというWindowsのGUIアプリで分析できる。
- が、WinCacheGrindの使い方がイマイチ難しいので、Xdebug1系で十分な気がする。

## インストール

- インストールされるバイナリは、ライブラリファイル1個だけ。
- perar install xdebug- betaしてもいいが、今回はソースからインストールした。
- ソースインストールは、./configure;make;make installはOKだった。
- インストール後は、php.iniにextension="/some/where/xdebug.so"などと設定する。
- プロファイリングの細かい設定は、php.iniにも書けるが、.htaccessでphp_valueで指定した方が手軽でよい。

## プロファイル（Xdebug1系）

- ファイルに自動的に書き出すオートプロファイルと、PHPスクリプトにXdebug関数を挿入するマニュアルなプロファイルがある。
- オートプロファイルは見やすいフォーマットで出力してくれるので、これを利用した。
- オートプロファイルには9つのモードがあり、出力内容が違う。
- 関数ごとにまとめた、XDEBUG_PROFILER_FS系のモードが分析に都合がいいだろう。
- XDEBUG_PROFILER_SD系は時系列（行系列）なので、Mapleでは結果ファイルが1万行を超えて、そのままでは使いづらい。
- ので、時系列（行系列）のモードは、部分的にプロファイルするか、結果ファイルを加工することになるだろう。

## オートプロファイルの設定（Xdebug1系）

- .htaccessに以下の項目を追加する。

```ini
 php_value xdebug.auto_profile 1
 php_value xdebug.auto_profile_mode 3
 php_value xdebug.output_dir '/some/where'
```

## 注意点

- 測定ごとに結構ブレがある。特に最初の測定では、mod_phpがPHPスクリプトをコンパイルする時間をとられて遅くなる。
- 他にもsmartyのキャッシュも影響するようだ。
- number of callsというキーワードが出てくるが、時系列（行系列）でのプロファイルの場合と関数ごとにまとめたプロファイルの場合で、意味が違う。
- 時系列（行系列）のプロファイルの場合、その行でその関数が2回続けば、「2」とされる。
- 例えば、trim($str);trim($str);という行があれば、trim()のnumber of callsは2になる。
- 関数ごとにまとめたプロファイルの場合、リクエスト中にその関数が呼ばれた回数。

## 参考URL
Xdebug公式

- http://xdebug.org/index.php

WinCacheGrind（Xdebug2のログをグラフ化する）

- http://sourceforge.net/projects/wincachegrind/

Xdebugの簡単な使い方（日本語）

- http://winofsql.jp/VA003334/php051120172152.htm
- http://bobchin.ddo.jp/wiki/index.php?PHP%2F%A5%C7%A5%D0%A5%C3%A5%B0%2FXdebug
