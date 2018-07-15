# 統計情報の計算 - Measure-Object

## エイリアス

```powershell
measure -> Measure-Object  
```

## ファイルサイズの合計

```powershell
gci *.txt | Measure-Object
```

```powershell
gcl | Measure-Object Length -Sum | % { $_.Sum / 1KB }
```

## フォルダサイズを求める

```powershell
gci * | Add-DirectoryLength | ft -Property name,length 
```

PS標準では無理なので、http://pscx.codeplex.com/よりPscxをインストールしてAdd-DirectoryLengthコマンドレットを使う。


## 参考
http://technet.microsoft.com/ja-jp/library/ee176900.aspx
