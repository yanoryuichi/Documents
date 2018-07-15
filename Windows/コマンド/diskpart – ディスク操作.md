# diskpart - ディスク操作

## ドライブ一覧

```powershell
echo list volume | diskpart
```

## マウント

```powershell
diskpart             # (0)
> list volume        # (1)
> select volume 3    # (2)
> assign letter=f    # (3)
```

(0)でDiskpartを起動、(1)でボリューム一覧の確認、(2)でボリュームを選択、(3)でFドライブに割り当て。

## アンマウント

```powershell
diskpart
> list volume
> select volume 3
> remove all dismount
```

## 選択しているボリュームの確認

```powershell
> list volume
```

↓先頭に「*」マークがある。

```powershell
  Disk ###  Status           Size     Free     Dyn  Gpt
  --------  ---------------  -------  -------  ---  ---
  Disk 0    オンライン        233 GB  1012 MB
  Disk 1    オンライン         75 GB   314 MB
  Disk 2    オンライン        233 GB      0 B
* Disk 7    オンライン       5726 MB      0 B
```

## MBR（またはEFI）のシステムパーティションの設定

```powershell
diskpart
> list disk
> select disk 0
> list partition
> select partition 1
> active
> exit
```

この例ではパーティション1がシステムパーティションとしてアクティブになり、MBR（またはEFI）はこのパーティションを使ってシステムをブートしようとするようになる。

## MBRの消去

```powershell
diskpart
> list disk
> select disk 0
> clean
> exit
```

### 参考
http://www.atmarkit.co.jp/fwin2k/win2ktips/1294dskclean/dskclean.html

## パーティション（ボリューム）の作成

```powershell
diskpart
> list disk                            # ディスク一覧を確認
> select disk 2                        # 新規追加したディスクを選択する（ここでは2）
> lisst partition                      # パーティションを確認（ここでは何もない）
> create partition primary             # パーティションを作成（プライマリディスクとして全サイズ割り当て）
> list vol                             # ボリュームを確認
　　　　　　　　　　　　　　           # ファイルシステムがRAW、ドライブレター無しで今作成したパーティションが確認出来る
> select vol 4                         # 今作成したボリュームを選択（ここでは4）
> format fs=ntfs label="MYHDD01" quick # NTFSでクイックフォーマットする
> assign letter=g                      # レタードライブを割り当て（ここではGドライブ）
> list vol                             # ボリュームを確認
```

## インストールUSBメモリの作成
http://www.atmarkit.co.jp/ait/articles/1305/20/news087.html

## 参考

- http://support.microsoft.com/kb/300415/ja
- http://www.atmarkit.co.jp/fwin2k/win2ktips/1115dpartcmd/dpartcmd.html
