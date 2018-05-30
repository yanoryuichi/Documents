# IIS8 インストール

## インストール方法

- The Server Manager user interface in Windows Server 2012 R2
- A command-line installation using DISM (Deployment Image Servicing and Management)
- A command-line installation using PowerShell cmdlets

## Windows Server 2012 R2にサーバーマネージャーを使ってインストールする

- サーバーマネージャを起動する。
- ダッシュボードを選ぶ。
- 「管理」から「役割と機能の追加」を選ぶ。
- 「開始する前」にで次へを選ぶ。
- 「インストールの種類」で「役割ベースまたは…」を選ぶ。次へ。
- 「サーバーの選択」で「サーバープールからサーバーを選択」を選ぶ。次へ。
- 「サーバーの役割」で「Webサーバー（IIS）」を選ぶ。
  - 関連する機能追加のポップアップが出るので「機能の追加」を選ぶ。
- 「サーバーの役割」で次へを選ぶ。
- 「機能」で「.NET 3.5」「.NET 4.5」「ASP.NET 4.5」を選ぶ。次へを選ぶ。
- 「Webサーバの役割」で次へを選ぶ。
- 「役割サービス」で以下を選ぶ。次へ。
  - 「Webサーバー」→「セキュリティ」以下の項目を全て選ぶ。
  - 「アプリケーション開発」→「.NET 拡張機能 4.5」「ASP.NET 4.5」「ISAPI」を選ぶ。
  - 「管理ツール」→「管理サービス」を選ぶ。
- 「確認」で「必要に応じて対象サーバを自動的に再起動する」を選ぶ。「インストール」を選ぶ。
- インストールはしばらく時間が掛かる。終わったら、「閉じる」を選ぶ。
- ブラウザを起動して、http://localhost にアクセスしてみる。青い画面が表示される。

## 参考
http://www.iis.net/learn/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2
