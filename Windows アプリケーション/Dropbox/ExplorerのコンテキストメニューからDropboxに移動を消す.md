# ExplorerのコンテキストメニューからDropboxに移動を消す

## Dropboxに移動

- Dropboxアプリをインストールすると、Explorerのコンテキストメニューに"Dropboxに移動"という項目が加わり、非常に目障り。
- Dropboxアプリの設定画面から削除する機能は用意されていない。Dropboxのウェブサイトに削除する方法は説明されてない。
- こういう悪質な事は止めてもらいたい。

## 手順

- タスクトレイからDropboxのアイコンをクリック→右上の歯車→Dropboxを終了を選び、Dropboxを終了する。
- デスクトップやスターメニューにある、Dropboxのショートカットアイコンを右クリックして、プロパティを選ぶ。
- リンク先に"-move-to-dropbox=False"という記述を加える。例えば以下のようになる。

```
 - "C:\Program Files (x86)\Dropbox\Client\Dropbox.exe" /home -move-to-dropbox=False
```

- そのショートカットアイコンをダブルクリックして、Dropboxを起動する。
- ExplorerのコンテキストメニューからDropboxに移動をが消えているはず。
- 消えてない場合は、エクスプローラーを再起動する。（もしくはサインインしなおす）

## 参考
http://www.intowindows.com/how-to-remove-move-to-dropbox-from-context-menu/
