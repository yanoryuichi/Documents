# IIS8にウェブサイトを追加

- IISマネージャーを起動する。
- 左ペインの「サイト」を右クリックして「Webサイトの追加」を選ぶ。
- 以下の項目を入力する。
  - サイト名 test-site-1
  - 物理パス c:\inetpub\test-site-1
  - ホスト名 test-site-1.example.com
- 物理パスで指定したフォルダにindex.htmlファイルを作成する。
- ブラウザでhttp://test-stie-1.example.com/にアクセスする。

## 参考

- http://technet.microsoft.com/ja-jp/library/cc772350(v=WS.10).aspx
- http://www.iis.net/learn/manage/creating-websites/scenario-build-a-static-website-on-iis
- http://awoni.net/personal-site/web-site/
- http://technet.microsoft.com/en-us/library/hh831550.aspx
