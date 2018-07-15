# Where-Object

## 基本

```powershell
Get-ChildItem | Where-Object { $_.Extension -eq '.txt' }
```

## 省略形

```powershell
Get-ChildItem | ? { $_.Extension -eq '.txt' }
```

## さらに省略

```powershell
dir | ? Extension -eq '.txt'
```

## ワイルドカード

```powershell
dir | ? Name -Like '*.txt'
```

## 正規表現

```powershell
dir | ? Name -Match '\.txt$'
```

## 複数条件
### OR検索

```powershell
dir -Recurse | ? { $_.Extension -eq ".jpg" -or $_.Extension -eq ".gif" }  
```

### AND検索

```powershell
dir -Recurse | ? { $_.Extension -eq ".txt" -and $_.Length -ne 0 }  
```

## テキストファイル内容の検索
Select-Stringを使う。

## 参考
http://technet.microsoft.com/ja-jp/library/dd347549.aspx
