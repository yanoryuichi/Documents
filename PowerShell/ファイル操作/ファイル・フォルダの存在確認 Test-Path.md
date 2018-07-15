# ファイル・フォルダの存在確認 Test-Path

### ファイルが存在するか？

```powershell
Test-Path .\1.txt -PathType Leaf
```


### フォルダが存在するか？

```powershell
if (!(Test-Path .\dir1 -PathType Container)) {
  echo "Not"
}
```

### パスが存在するか？

```powershell
$dir = Join-Path $env:USERPROFILE "Dropbox"
$file = 1.txt
$path = Join-Path $dir $file

if (Test-Path $path) {
  echo "OK"
}
```

### いずれか1つはファイルが存在するか？

```powershell
$files = @("1.txt", "2.txt", "3.txt")

if (($files | % { Test-Path $_}) -contains $true) {
    echo "Ok"
} else {
    echo "Not"
}
```

## 参考

Test-Path 
: https://technet.microsoft.com/en-us/library/hh849776.aspx

Using Test-Path to Verify the Existence of an Object 
: https://technet.microsoft.com/en-us/library/ff730955.aspx
