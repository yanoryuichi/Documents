# Get-Date


## 日付を加算する（減算する）

```powershell
$today = Get-Date
$tomorrow = $today.AddDays(1)
```

```powershell
Write-Host (Get-Date).AddDays(-7)
```

## 曜日を数値で取得する

```powershell
$str = (Get-Date).DayOfWeek         # => Sunday
$num = [Int] (Get-Date).DayOfWeek   # => 0
```

## 参考
https://technet.microsoft.com/en-us/library/ff730960.aspx
