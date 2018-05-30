# Hyper-V Serverインストール

## 手順
### ISOファイルの入手とインストール

- MSのサイトからHyper-V ServerのISOファイルをダウンロードする。
- USBメモリにコピーするかDVDに焼いて、ブートディスクを作る。
  - [[Windows 7 USB/DVD download tool>Windows/お気に入りアプリ/ユーティリティ]]を使うと便利。
- ブートディスクをサーバにセットして、サーバを起動、インストール作業を行う。プロダクトキー等は不要で、特に迷う箇所はない。

### Hyper-V Serverの設定

- Hyper-V Serverを起動する。
- 青い画面のsconfigが起動しているので、以下の設定を行う。
  - コンピュータ名
     - 適当な名前を付ける。
  - リモート管理の構成
     - リモート管理を有効にする。
  - 更新プログラムのダウンロードとインストール
     - 一通り全部アップデートする。
  - リモートデスクトップ
     - リモートデスクトップを有効にする。
  - ネットワーク設定
     - 通常は静的にIPアドレスを設定する。

### 管理用PCからリモートデスクトップで接続する
### 管理用PCからHyper-Vマネージャーで接続する

- 管理ツールのコンポーネントサービスを起動し、マイコンピューターを右クリックしてプロパティを開き、 COMセキュリティタブにあるANONYMOUS LOGOINでアクセス許可でリモートにチェックを入れる。

## 参考

- [[[Hyper-V体験記] 仮想化環境を理解し、無償のHyper-V Serverを試す>http://news.mynavi.jp/articles/2011/06/13/goto02/menu.html]]
- [[[Hyper-V体験記]無償のHyper-V ServerでWindows/Linuxを稼動させる>http://news.mynavi.jp/articles/2011/06/13/goto02/menu.html]]
- Microsoft Hyper-V Server 2008 R2
  - http://www.microsoft.com/japan/servers/hyper-v-server/default.mspx
- Windows 7 Service Pack 1 (SP1) 用のリモート サーバー管理ツール
  - http://www.microsoft.com/downloads/ja-jp/details.aspx?FamilyID=7d2f6ad7-656b-4313-a005-4e344e43997d
