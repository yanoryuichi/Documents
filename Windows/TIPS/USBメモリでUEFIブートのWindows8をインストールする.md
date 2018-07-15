# USBメモリでUEFIブートのWindows8をインストールする

## 注意点

- USBメモリはNTFSではなくFAT32でフォーマットしないとUEFIが認識しない。
- よって、Windows 7 USB DVD Download Toolは強制的にNTFSになる為に不適切。
- diskpartコマンドを使って、インストールUSBメモリを作成する。

## インストールUSBメモリ（UEFI）の作成
### diskpartコマンドによる
http://www.atmarkit.co.jp/ait/articles/1305/20/news087.html
### Rufusによる
http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html

## Windows 8のインストール
http://internet.watch.impress.co.jp/docs/column/shimizu/20121002_563382.html

## 参考
http://www.atmarkit.co.jp/ait/articles/1404/18/news088.html
