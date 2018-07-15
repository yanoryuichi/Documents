# assoc ( ftype ) - 拡張子の関連付け

## 拡張子とファイルタイプの基礎知識

- 拡張子.txtではレジストリにHKEY_CLASSES_ROOT\.txtというキーが存在し、既定の値txtfileが設定されている。このtxtfileをファイルタイプと言う。
- ファイルタイプtxtfileはレジストリHKEY_CLASSES_ROOT\txtfileというキー以下で各種設定がされる。

## 拡張子に関連付けられているファイルタイプの確認

```powershell
assoc            # 全拡張子のファイルタイプ一覧
assoc .xlsx      # .xlsx拡張子に関連付けられているファイルタイプ
```

## ファイルタイプに対して起動するプログラムの確認

```powershell
ftype                  # 全ファイルタイプに対する起動するプログラム一覧
ftype Excel.Sheet.12   # ファイルタイプ"Excel.Sheet.12"に対する起動するプログラム
```

## 起動するプログラムを変更する
### 現在のプログラムの確認

```powershell
assoc .txt                  # => .txt=txtfile
ftype txtfile               # => txtfile=%SystemRoot%\system32\NOTEPAD.EXE %1
```

### プログラムの変更

```powershell
ftype txtfile="C:\App\gvim.exe" "%1"
```

拡張子.txtに関連付けられているプログラムをnotepad.exeからgvim.exeに変更する例。


## 参考

- http://www.atmarkit.co.jp/fwin2k/win2ktips/841ftypes/ftypes.html
- http://blogs.technet.com/b/stanabe/archive/2010/05/25/handling-file-associations-with-command-line.aspx
- http://homepage2.nifty.com/suyamsoft/Registry/Explorer/Association/index.html
- http://ascii.jp/elem/000/001/195/1195074/
