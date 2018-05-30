# Disk2vhdでGPTディスクをP2Vする

## 概要

- UEFIブートのマシン（GPTディスク）をDisk2vhdでP2Vしようとしても、Hyper-V上でエラーが発生し、仮想マシンを作成できない。
- これを避けるためには、P2VしてVHDXファイルを作った後、GPTからMBRへ変換し、BCDストアを作り直す必要がある。
- 以下にその手順を示すが、bootrecコマンドやdiskpartコマンドの概要程度はあらかじめ知っておいた方がいい。
  - [[スタートアップ修復（MBR修復）>http://yanor.net/wiki/?Windows%2F%E8%B5%B7%E5%8B%95%2F%E3%82%B9%E3%82%BF%E3%83%BC%E3%83%88%E3%82%A2%E3%83%83%E3%83%97%E4%BF%AE%E5%BE%A9%EF%BC%88MBR%E4%BF%AE%E5%BE%A9%EF%BC%89]]

## 手順

### 1. Disk2vhdでVHDXファイルを作成する

- 対象のPCにログインして、Disk2vhdをインストール、起動する。
- Disk2vhdでGPTディスクをVHDXファイルに変換する。（VolumeShadowCopyとVHDXにチェックを入れる。）
  - https://technet.microsoft.com/en-us/sysinternals/ee656415

### 2. VHDXファイルをマウントしてGPTからMBRへ変換する

- VHDXファイルを別のPCに移す。（同一PCではVHDXファイルをマウントしようとすると重複エラーが発生するので。）
- そのPCでVHDXファイルをマウントする。（VHDXをマウントするにはWindows 8以上が必要。）
- EaseUS Partition MasterのようなGPTをMBRへ変換できるソフトを用意する。（OS標準のディスク管理ツールではMBRへの変換の際にディスク内容が消去される。）
  - http://forest.watch.impress.co.jp/library/software/easeuspart/
- EaseUS Partion Masterの場合、アプリを起動して、VHDXファイルによるドライブを選択して、右クリックして、MBRへの変換を行う。
- そのドライブにある、ブートパーティションや回復環境パーティションは削除して、Windowsパーティションだけの状態にする。

### 3. Hyper-Vで仮想マシンを作成する

- Hyper-Vの稼働しているマシンにログインして、Hyper-Vマネージャで仮想マシンを作成する。
- マシンの世代は第1世代を選んで作成する。
- アタッチするディスクは上で作成してMBRへ変換したVHDXファイルを選択する。

### 4. 仮想マシンのBCDストアを修復する

- Windowsのインストールディスクなど、リカバリ環境のISOファイルを用意する。
  - Windows 評価版 https://www.microsoft.com/ja-jp/evalcenter/
- Hyper-Vマネージャで上の仮想マシンの設定を変更し、DVDに上のISOファイルを設定する。
- 仮想マシンを起動し、DVDからブートし、Windowsインストーラーを起動する。
- Windowsインストーラーで、インストールは行わず、「コンピュータを修復する」を選ぶ。
- 「トラブルシューティング」→「詳細オプション」→「コマンドプロンプト」を選ぶ。
- diskpartコマンドを使って、VHDXファイルドライブのパーティションをアクティブにする。詳細は以下だが、diskpartコマンドについてはあらかじめ理解しておくこと。

```clike
diskpart 
list disk 
select disk 0 
list partition 
select partition 1 
active 
exit
```

- bootrecコマンドを使って、BCDストアを修復する。詳細は以下。

```clike
bootrec /fixmbr
bootrec /fixboot 
bootrec /rebuildbcd 
```

- exitコマンドでコマンドプロンプトを終了する。
- リカバリ環境に戻ったので、コンピューターの電源を切るを選ぶ。

### 5. Windowsの起動の確認

- Hyper-Vマネージャで上の仮想マシンの設定を変更し、DVDからメディアをイジェクトする。
- 仮想マシンを起動して、Windowsの起動を確認する。

## 参考

- https://4sysops.com/archives/how-to-p2v-windows-server-2012-r2-with-uefi-and-a-gpt-disk/
- https://www.quora.com/How-do-I-convert-GPT-into-MBR
- http://www.partition-tool.com/resource/GPT-disk-partition-manager/convert-gpt-disk-to-mbr-disk.htm
- https://technet.microsoft.com/en-us/sysinternals/ee656415
- [[スタートアップ修復（MBR修復）>http://yanor.net/wiki/?Windows%2F%E8%B5%B7%E5%8B%95%2F%E3%82%B9%E3%82%BF%E3%83%BC%E3%83%88%E3%82%A2%E3%83%83%E3%83%97%E4%BF%AE%E5%BE%A9%EF%BC%88MBR%E4%BF%AE%E5%BE%A9%EF%BC%89]]
