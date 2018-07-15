# TortoiseSVN 多段SSH接続

- PuTTYをインストールする。
- PuTTYでローカルProxyCommandを使って多段SSH接続するセッション情報を作る。（RemoteCommandではダメ。ダイナミックポートフォワードならOKかも？）
- TortoiseSVNでSSHクライアントにTortoisePlink.exeを指定して、SVNリポジトリにアクセスする場合は、URLのホスト名を上のセッション情報にする。
- また、TortoisePlink.exeから呼び出すセッションの中でローカルProxyCommandを設定している場合、TortoisePlink.exeまたはplink.exeはフルパスで記述するか、環境変数PATHに含まれている必要がある。


## 参考
### PuTTYのローカルProxyCommandを設定する方法
このサイトのどこかに書いてるので参考にする。

### TortoiseSVNでPuTTYのセッション情報を使う方法
このサイトのどこかに書いてるので参考にする。
