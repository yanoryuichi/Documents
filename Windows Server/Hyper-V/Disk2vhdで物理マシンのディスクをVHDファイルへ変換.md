# Disk2vhdで物理マシンのディスクをVHDファイルへ変換

## Disk2vhdとは？

- 起動中の物理マシンの起動ディスクをVHDファイルへ変換して、Hyper-Vなどの仮想化環境のゲストOSとして稼働させる（P2V）ことが出来る。
  - VHDファイルへの変換時にディスクコントローラーなどのHALを仮想環境向けに書き換える事によって仮想化対応している。
- ボリュームシャドウコピーを使うので、起動中でも安全に完全なバックアップを取ることが出来る。

### Disk2vhd ダウンロード

- http://technet.microsoft.com/en-us/sysinternals/ee656415

## 手順

- Disk2vhdをダウンロードして、対象の物理マシンで実行する。
- バックアップを取る全てのディスクにチェックを付ける。
  - ドライブレターのないブートディスクにもチェックを付ける。
- Use VHDXにチェックを付ける。（VHDXは新しい形式で、通常こちらを選んだ方が良い）
- User Volume Shadow Copyにチェックを付ける。（より安全なトランザクションコピーが行われる）
- VHD(X)ファイルの保存場所は、バックアップを取らないディスクにした方が安全。従って、外付けHDDなどを用意して、接続した方が良い。

### 参考

- https://hyperv.veeam.com/blog/how-to-convert-physical-machine-hyper-v-virtual-machine-disk2vhd/
- http://www.microsoft.com/ja-jp/techfielders/column.aspx
- http://blogs.technet.com/b/osamut/archive/2011/02/28/3390534.aspx

## Hyper-Vの仮想マシンを作成する際の注意点

- ゲストOSがWindows8の場合でも、仮想マシンを第2世代にするとブートに失敗するようだ。
- 第1世代で作成する事。

## UEFIブートの物理マシンをP2Vするには？

- UEFIブートではパーティション情報がMBRでなくGPT形式だが、現在のDisk2vhdはGPTを認識できない。
- 従って、一旦、ディスクコピーを取った後、GPTからMBRへ変換する必要がある。
- 詳しくは、https://4sysops.com/archives/how-to-p2v-windows-server-2012-r2-with-uefi-and-a-gpt-disk/ を参考にする。
- https://www.youtube.com/watch?v=DDaSFRAviq4
