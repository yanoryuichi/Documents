# PowerShell ファイル検索 ファイル数をカウント

## ファイルとディレクトリ数をカウント

```powershell
dir -Recurse | measure
```

```powershell
Count    : 5
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

## ファイル数をカウント

```powershell
dir -Recurse -File | measure
```

```powershell
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```
