# xargs

Foreach-Object(%)を使う。

### 例えば１から3までを出力して

```powershell
PS> 1..3
1
2
3
```

### %でループさせて0パディングを適用する

```powershell
PS> 1..3 | % ToString('00')
01
02
03
```

### 省略をしない%(Foreach-Object)の書式

```powershell
1..3 | % { $_.ToString('00') }
1..3 | ForEach-Object { $_.ToString('00') }
```
