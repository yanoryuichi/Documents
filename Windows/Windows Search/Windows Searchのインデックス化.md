# Windows Searchのインデックス化

## インデックス属性
http://news.mynavi.jp/column/win81tips/027/

## attribコマンドでインデックス属性を確認・設定する
### 確認

```powershell
C:\doc>attrib
A       I    C:\doc\bar.txt
A            C:\doc\foo.txt
```

"I"は"非インデックス対象ファイル属性"なので、bar.txt内のコンテンツはインデックス化されない（検索されない）。但し、ファイル名は検索される。

### 設定

```powershell
C:\doc>attrib -I bar.txt
C:\doc>attrib +I foo.txt
C:\doc>attrib
A            C:\doc\bar.txt
A       I    C:\doc\foo.txt
```

これで、bar.txtのコンテンツは検索され、foo.txtのコンテンツは検索されなくなった。

### 参考
http://www.atmarkit.co.jp/fwin2k/win2ktips/1134attribn/attribn.html
