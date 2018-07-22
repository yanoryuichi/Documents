# NKFでEUC-JPのファイルを自動で文字コード変換する

## 前提

- Windows上で文字コードがEUC-JPのファイルを扱う事とする。
- Windows上ではSJISが基本になるので、TotroiseHGでEUC-JPのファイルを開く際にSJISに変換する必要がある。
- WindowsにNKFをインストールして、それを利用する。

## NKFのインストール
### NKFの入手

- 以下よりNKFをダウンロードする。
- http://www.vector.co.jp/soft/win95/util/se295331.html

### NKFの確認

- ダウンロードしたZIPファイルを展開して、以下のnkf.exeファイルを確認する。
- nkfwin\vc2005\win32(98,Me,NT,2000,XP,Vista,7)ISO-2022-JP\nkf.exe

### NKFのフォルダの作成

- NKFを設置するフォルダをユーザプロファイル以下に作成する。
- 以下はその例だが、別の場所、別の名前で作成しても構わない。

```clike
例： C:\Users\taro\App
```

### NKFのコピー

- nkf.exeを上で作成したフォルダにコピーする。

### 実行パスの追加

- コントロールパネルを起動して、[システムとセキュリティ]→[システム]を開く。
- [コンピューター名、ドメインおよびワークグループの設定]の項目にある[設定の変更]のリンクを押下する。
- システムのプロパティウィンドウが開くので、[詳細設定]タブを選び、[環境変数]ボタンを押下する。
- [ユーザーの環境変数]の変数に[Path]が存在するか確認する。存在すれば、それを選択して[編集]ボタンを押下する、存在しなければ、[新規]ボタンを押下する。
- 新しいユーザー変数またはユーザー変数の編集ウィンドウが開くので、以下の例のように入力する。変数値は上で作成したnkfのフォルダのパスにする。
  - 変数名： Path
  - 変数値： C:\Users\taro\App\
  - （すでに変数値が存在している場合は次のように";"でつなげる： C:\Users\taro\;C:\Users\taro\App\）
- [OK]を押して、すべてのウィンドウを閉じる、

### PCの再起動

- PCを再起動する。

### nkfの実行確認

- （Windowsキー+Rを押下して、"cmd"と入力してEnterキー押下する等して）コマンドプロンプトを起動する。
- "nkf --version"と入力してEnterキーを押下して、以下のようなメッセージが表示されればnkfの実行が確認される。

```clike
C:\Users\taro>nkf --version
Network Kanji Filter Version 2.1.1 (2010-08-08)
Copyright (C) 1987, FUJITSU LTD. (I.Ichikawa).
Copyright (C) 1996-2010, The nkf Project.
```

## 文字コード変換の設定

- EUC-JPのファイルが含まれるプロジェクトのリポジトリフォルダを開き、.hgフォルダを開く。
- hgrcというファイル名のファイル（拡張子なし）を作成して（すでにあればそれをそのまま）、テキストエディタで開く。
- 以下の内容を追加して記述し、保存し、ファイルを閉じる。

```clike
[decode]
**.html = pipe: nkf -S -e
**.php = pipe: nkf -S -e
**.txt = pipe: nkf -S -e

[encode]
**.html = pipe: nkf -E -s
**.php = pipe: nkf -E -s
**.txt = pipe: nkf -E -s
```

- これでこのリポジトリのHTML/PHP/TXTファイルはEUC-JPからSJISへ相互に変換される。

## 参考

- http://d.hatena.ne.jp/flying-foozy/20111215/1323944808
- http://d.hatena.ne.jp/flying-foozy/20140102/1388624842
