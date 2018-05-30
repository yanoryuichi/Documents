# 統合サービス for Linux

- 以下から、PDFのReadMeとISOファイルをダウンロードする。
  - http://www.microsoft.com/downloads/ja-jp/details.aspx?FamilyID=216DE3C4-F598-4DFF-8A4E-257D4B7A1C12
  - http://www.microsoft.com/ja-jp/download/search.aspx?q=Linux+Integration+Services+Version
- USBメモリやDVDにコピーして、Hyper-Vサーバに挿入する。
- Hyper-VマネージャでゲストOSのDVDの設定を変更し、上のISOファイルを指定する。
- ゲストOSにログインして、DVDをマウントする。

```clike
mkdir -f /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
```

- DVDの中のシェルスクリプトを実行する。RPMパッケージがインストールされる。
- リブートする。

## CentOSでCDROMドライブを認識しない場合
/dev/cdromが見つからない場合は以下のコマンドを実行する。

```clike
insmod /lib/modules/$(uname -r)/kernel/drivers/ata/ata_piix.ko
```

その後、以下のコマンドでCDROMをマウントする。

```clike
mount /dev/cdrom /mnt/cdrom
```
