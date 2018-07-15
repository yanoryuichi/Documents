# Windows To GoをEnterprise以外で作る

## 概要

- Windows To GoはUSBメモリ（もしくはUSBドライブ）にWindowsをインストールして、USBメモリからWindowsを起動する機能。
- Windows To GoはWindows 8のEnterpriseエディションのみに備わっており、同エディションではコントロールパネルからWindows To GoなUSBメモリを簡単に作れる。
- Windows To GOなUSBメモリのOSライセンスはEnterpriseエディションのアドオンライセンスになっており、新たに追加のライセンスは必要とされない。
- しかし、インストールされたWindows To Goは新しいPCに接続してOSを起動する度にOSのアクティベーションが必要になり、マルチ認証ライセンスの上限回数を使い切ってしまう事が考えられる。
- そこで、EnterpriseエディションのWindows To Go機能を使わずに、無印Windows 8やWindows 8 ProでWindows To Go（とだいたい同じ機能）を行う方法を説明する。

## 必要なもの

- Windows 8がインストールされたPC
- USB接続のHDDもしくはSSD（USBメモリでは試していない）
- リテール版のWindows 8のインストールディスク（もしくはISOファイル）

## 手順

- USBドライブを初期化する。
- Windows 8のインストールディスクからInstall.wimファイルを取り出す。
- Windows 8.1 Windows Assessment and Deployment Kit（ADK）をMSのサイトからダウンロードする。
- ADK付属のimagexコマンドでInstall.wimをUSBドライブにコピーする。

詳細な手順は参考のウェブページを見る事。

## 補足

- この方法で作られたUSBドライブのWindowsは、あくまでもWindows To Go（の一種）としてシステムで認識されているようで、通常のWindowsと比較して若干制限がある。
- 例えば、通常ならWindows 8はWindowsストアから8.1へアップグレード出来るが、Windows To Goの場合、出来ない。
- それ以外にもUSB接続されている為に制限がいくつかある。

## 参考
http://www.tomshardware.com/faq/id-1867613/create-windows-drive-windows-enterprise.html
