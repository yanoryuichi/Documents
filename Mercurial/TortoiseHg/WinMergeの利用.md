# WinMergeの利用

## WinMergeのインストールとWinMergeU.exeファイルパスの確認

- 今回は日本語版WinMergeの32ビット版をインストールする。
  - 参考： [[Windows/アプリケーション/WinMerge]]
- インストール後、WinMergeU.exeのパスを確認する。今回は以下の通り。

```clike
"C:\Program Files (x86)\WinMerge\WinMergeU.exe"
```

## mercurial.iniファイルパスの確認

- エクスプローラーで適当なフォルダを開き、右クリックして、Hg Workbenchを起動する。
- [ファイル]->[設定]を開く。
- 画面上部の[設定ファイル： ...]にあるmercurial.iniファイルパスを確認する。今回は以下の通り。

```clike
C:\Users\taro\AppData\Roaming\mercurial.ini
```

## mercurial.iniの編集

- メモ帳等のエディタでmercurial.iniを開く。
- 以下のように編集する。

```clike
[extensions]
extdiff=

[extdiff]
cmd.wmdiff = C:\Program Files (x86)\WinMerge\WinMergeU.exe
opts.wmdiff = /r /e /x /ub

[merge-tools]
winmerge.args = /e /ub /dl other /dr local $other $local $output
winmerge.regkey = Software\Thingamahoochie\WinMerge
winmerge.regname = Executable
winmerge.fixeol = True
winmerge.checkchanged = True
winmerge.gui = True
```

- 保存してエディタを終了する。

### 編集時の注意点

- [extensions]等の項目に設定群がすでに存在する場合は、既存の設定群の下の行に設定を記述する。項目がない場合はこの通りに記述する。
- また、ここで記述している設定の"wmdiff"や"winmerge"は任意だが、同じ名前を使ってはいけない。すなわち、[merge-tools]でwinmerge.args=...として、[extdiff]でcmd.winmerge=...としてはいけない。cmd.wmdiff=...のように別の名前を使う。

## WinMerge利用の設定

- エクスプローラーで適当なフォルダを開き、右クリックして、Hg Workbenchを起動する。
- [ファイル]->[設定]を開く。
- 画面左部の項目群から[TortoiseHg]をクリックする。
- 画面右部の設定を以下のようにする。
  - 3-way マージツール winmerge
  - GUI 差分表示ツール wmdiff
- 画面左部の項目群から[エクステンション]をクリックする。
- 画面右部の設定で[extdiff]にチェックが入っているのを確認する。
- [OK]を押下して、設定ウィンドウを閉じる。
- Hg Workbenchを閉じる。

## 追記
TortoiseHg 2.5あたり以降からは、先にWinMergeをインストールして次にTortoiseHgをインストールすれば（？）、iniファイルに設定をしなくてもWinMergeが利用できるっぽい。よって、↑に長々と書いた説明はすでに不要っぽい。
