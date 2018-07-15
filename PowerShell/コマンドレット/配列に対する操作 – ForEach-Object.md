# 配列に対する操作 - ForEach-Object

## エイリアス

```powershell
1,2,3 | ForEach-Object { New-Item -type f ([String] $_ + ".txt") }  
1,2,3 | foreach { New-Item -type f ([String] $_ + ".txt") }  
1,2,3 | % {  New-Item -type f ([String] $_ + ".txt") }  
```

```powershell
=> 1.txt 
   2.txt 
   3.txt 

```

## Where-Objectと組み合わせて

```powershell
1..6 | ? { $_ % 2 -eq 0 } | % { "DEBUG: " + $_ } 
```


```powershell
=> DEBUG: 2 
   DEBUG: 4  
   DEBUG: 6
```

## Begin/Process/Endブロック

```powershell
dir *.txt | % -Begin { $sum = 0 } -Process { $sum += $_.length } -End { "File Size: " + $sum + " bytes" }
```

## 参考
http://technet.microsoft.com/ja-jp/library/dd347608.aspx
