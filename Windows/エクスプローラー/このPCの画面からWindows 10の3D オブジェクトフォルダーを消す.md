# このPCの画面からWindows 10の3D オブジェクトフォルダーを消す

## 手順

- レジストリエディタを起動し、以下の項目を開き、{0DB7E03F-FC29-4DC6-9020-FF41B59E513A} というキーを削除する。
- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace
- HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace
- なお、32ビットWindowsを使っている場合は後者のHKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node...は存在しないので、削除は不要。

## 参考

https://www.howtogeek.com/331361/how-to-remove-the-3d-objects-folder-from-this-pc-on-windows-10/
