# FSMO役割を他のDCへ移行する

## 現ドメインコントローラと新ドメインコントローラが正常に動作している場合
### Active DirectoryスキーマMSCのセットアップ

- cmd.exeから以下を実行して、Active Directoryスキーマ管理スナップインをインストールする。
  - regsvr32 schmmgmt.dll
- mmc.exeを起動する。
- スナップインの追加と削除で、Active Directoryスキーマを追加する。


### Active Directoryドメインコントローラーの変更

- Active DirectoryスキーマMSCを起動する。
- なお、すでに新しいドメインコントローラーが選択されていた場合は以下の作業は不要。
- 左ペインの"Active Directoryスキーマ"を右クリックして、"Active Directoryドメインコントローラーの変更"を選ぶ。
- "次のドメインコントローラーまたはAD LDS..."にチェックを入れ、新しいドメインコントローラーのサーバを選択し、"OK"を押す。

### 操作マスターの変更

- 左ペインの"Active Directoryスキーマ"を右クリックして、"操作マスター"を選ぶ。
- 現在のスキーママスターが古いサーバである事、ターゲットスキーマが新しいサーバである事を確認して、"変更"を押す。

参考：

- http://www.atmarkit.co.jp/fwin2k/win2ktips/1172fsmotrans/fsmotrans.html
- http://dev.classmethod.jp/cloud/aws/active-directory-on-aws-4/

## 現ドメインコントローラがクラッシュ等で動作していない場合

- cmd.exeからntdsutilコマンドを実行する。以下、参考ページを参照の事。
- なお、@ITにある"fsmo maintenance: seize domain naming master …強制割り当て"は間違い（古いバージョン？）で、"domain"は不要。詳しくはntdsutilコマンド内で?を実行してヘルプを確認する事。

参考：

- http://blogs.technet.com/b/junichia/archive/2008/08/15/windows-server-dc.aspx
- http://network.station.ez-net.jp/server/microsoft/windows/dc_delete.asp
- https://technet.microsoft.com/ja-jp/library/cc816907(v=ws.10).aspx
- http://www.atmarkit.co.jp/fwin2k/win2ktips/1174fsmoseize/fsmoseize.html
