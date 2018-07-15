# ソート - Sort-Object

## 前提
### 1.csv:

```powershell
name,id1,id2
A,1,100
B,2,20
X,10,100
A,3,100
```

## 辞書順

```powershell
import-csv 1.csv | sort name | ft -auto
```

```powershell
name id1 id2
---- --- ---
A    3   100
A    1   100
B    2   20
X    10  100
```

## 数値順

```powershell
import-csv 1.csv | sort {[int]$_.id1},{[int]$_.id2} | ft -auto
```

```powershell
name id1 id2
---- --- ---
A    1   100
B    2   20
A    3   100
X    10  100
```

## 昇順・降順

### 昇順

```powershell
import-csv 1.csv | sort name | ft -auto
```

```powershell
name id1 id2
---- --- ---
A    3   100
A    1   100
B    2   20
X    10  100
```

既定では昇順でソートする。

### 降順

```powershell
import-csv 1.csv | sort -descending name | ft -auto
```

```powershell
name id1 id2
---- --- ---
X    10  100
B    2   20
A    3   100
A    1   100
```

### 昇順・降順組み合わせ

```powershell
import-csv 1.csv | sort @{Expression="name";Descending=$true}, @{Expression={[int]$_.id1};Ascending=$true} | ft -auto
```

```powershell
name id1 id2
---- --- ---
X    10  100
B    2   20
A    1   100
A    3   100
```

## 参考

- http://technet.microsoft.com/ja-jp/library/dd347688
- http://powershell.com/cs/blogs/ebookv2/archive/2012/03/12/chapter-5-the-powershell-pipeline.aspx
