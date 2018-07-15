# Windows 8のアプリの検索対象

## 既定の検索対象

- C:\ProgramData\Microsoft\Windows\Start Menu\Programs 以下のファイル
- C:\Users\All Users\Microsoft\Windows\Start Menu\Programs 以下のファイル
- %APPDATA%\Microsoft\WIndows\Start Menu 以下のファイル
- %PATH%の通ったフォルダ以下のファイル

## 自分で検索対象を追加する場合

- %APPDATA%\Microsoft\WIndows\Start Menu にアプリのショートカットを作る。
- もしくは、パスの通ったフォルダにアプリを置く。
- %APPDATA%\Microsoft\WIndows\Start Menu にシンボリックリンクを作ってもダメなようだ。

## 参考

- http://social.technet.microsoft.com/Forums/en-US/w8itprogeneral/thread/081ec2f2-cb81-4a1b-aae4-41ee8372d86b/
- http://pasofaq.jp/windows/mycomputer/shellfolder7.htm
