# 標準入力をファイルと標準出力に同時に出力 Tee-Object

### ファイルに出力

```powershell
dir | tee "C:\tmp\result.txt" | ft -a
```

### 変数に出力

```powershell
$result = $null
dir | tee -Variable result | ft -a
```

- 上の場合、$resultはSystem.IO.FileInfoオブジェクト。テキストではない。

## 参考
https://technet.microsoft.com/en-us/library/hh849937.aspx
