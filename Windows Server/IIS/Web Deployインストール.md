# Web Deployインストール

## Web Deployインストール手順
### IIS 管理サービスのインストール

- サーバマネージャーを起動する。
- 画面上の「管理」から「役割と機能の追加」ウィザードを開く。
- ウィザードに従ってサーバを選ぶ。
- 「サーバの役割」で「Webサーバー（IIS）」を選択してウィザードを進める。
- 「役割サービス」の項で「管理ツール」→「管理サービス」にチェックを入れる。
- 追加を完了する。

### Web Deployのダウンロード

- http://www.iis.net/downloads/microsoft/web-deploy
- 右上の「Install this extension」をクリックする。

### Web Deployのインストール

- ダウンロードしたインストーラーを実行してウィザードに沿ってインストールする。
- ウィザードでインストールする内容を聞かれるので「完全」を選ぶ。
  - 「標準」を選ぶと下の「管理サービスの委任」がインストールされないので。

## 発行プロファイルの作成

- IISマネージャーを開く。
- 左ペインで当該サーバを選択し、右ペインの「管理」に「管理サービスの委任」がある事を確認する。
- 当該サイトを右クリックして、「展開」→「Web 配置による発行の有効化」を選ぶ。
- 必要に応じてパラメータ（URL等）を修正する。
- 「設定」ボタンを押下する。
- 指定したフォルダに「XXX.PublishSettings」ファイルが出来る。

## 発行の実行

- ここではWebMatrixを使って発行を実行する。
- WebMatrixを起動する。
- 適当なサイトを作成する。
- 「発行」ボタンを押下する。
- 「発行プロファイルのインポート」を選ぶ。
- 先ほど作成した発行プロファイルを指定する。
- 「接続の検証」ボタンを押下して、接続を確認する。

## トラブルシューティング
http://blogs.msdn.com/b/masamis/archive/2010/02/15/msdeplytroubleshooting.aspx

## 参考

- http://www.orcsweb.com/blog/gabe/how-to-install-webdeploy-on-windows-server-2012/
- http://blogs.technet.com/b/bernhard_frank/archive/2011/09/01/configure-web-deploy-publishing-missing-in-iis-console.aspx
- http://uzulla.hateblo.jp/entry/2013/08/16/042416
- http://bartwullems.blogspot.jp/2012/06/iis-management-service-delegation-not.html
