# PowerShell ファイル検索 ファイルだけディレクトリだけ

## ファイルだけ

```powershell

dir -Recurse -File | select -First 10 FullName
```

## ディレクトリだけ

```powershell
dir -Recurse -Directory  | select -First 30 FullName
```

### 注意
上の-File -DirectoryはPS3.0以上で対応。

## 参考

http://superuser.com/questions/150748/have-powershell-get-childitem-return-files-only
