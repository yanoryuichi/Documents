# PowerShell ファイル検索 拡張子を取得

## ファイルから拡張子を取得

```powershell
dir -Recurse -File | select -First 10 FullName, Extension
```

```powershell
FullName             Extension
--------             ---------
C:\temp\001.jpg      .jpg
C:\temp\001.txt      .txt
C:\temp\002.txt      .txt
C:\temp\bar\test.txt .txt
```

## ユニークな拡張子をグループ化する

```powershell
dir -Recurse -File | group -Property Extension
```

```powershell
Count Name                      Group
----- ----                      -----
    1 .jpg                      {001.jpg}
    3 .txt                      {001.txt, 002.txt, test.txt}
```

```powershell
dir -Recurse -File | group -Property Extension | select name
```

```powershell
Name
----
.jpg
.txt
```
