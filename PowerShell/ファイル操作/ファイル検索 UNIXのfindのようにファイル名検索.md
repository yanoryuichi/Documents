# ファイル検索 UNIXのfindのようにファイル名検索

### ファイル名（フォルダ名）による再起検索

```powershell
dir -Recurse "*.js" | select -First 10 FullName
dir -Recurse -File "*index*" | select -First 10 fullname     # ファイルだけ
dir -Recurse -Directory "*img*" | select -First 10 fullname  # ディレクトリだけ
dir -Recurse "*.png","*.jpg" | select -First 10 fullname     # 複数のファイル名で
```

### 再帰検索でmaxdepthを指定する 1

```powershell

dir "*.txt" | select fullname                        # 直下のtxtファイル
dir "*.txt", "*\*.txt" | select fullname             # 直下のtxtファイルと直下のフォルダ内のtxtファイル
dir "*.txt", "*\*.txt", "*\*\*.txt | select fullname # 以降、同様
```

### 再帰検索でmaxdepthを指定する 2

```powershell
dir -Depth 1 | ? { $_.Name -like "*.txt" } | select fullname # 直下のtxtファイルと直下のフォルダ内のtxtファイル
dir -Depth 1  -Recurse -Filter *.txt | select fullname

 FullName
--------
C:\temp\1.txt
C:\temp\foo\2.txt
```

PS5.0以上 http://stackoverflow.com/questions/13249085/limit-get-childitem-recursion-depth

### 相対パスを取得

```powershell
dir -Recurse "*.txt"  | select -First 10 |  Resolve-Path -Relative
```

### CygpathでUNIX式の/区切りのファイル名へ変換

```powershell
dir -Recurse *.txt | % { cygpath.bat $_.FullName }
```

あらかじめcygpathはパスを調整しておくこと。
