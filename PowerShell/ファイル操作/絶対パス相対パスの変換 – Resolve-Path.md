# 絶対パス相対パスの変換 - Resolve-Path

## 相対パスを絶対パスへ変換

```powershell
PS tmp> Resolve-Path .\dir1\1.txt

Path
----
C:\tmp\dir1\1.txt
```

## 絶対パスを相対パスへ変換
### 1. 絶対パスを取得

```powershell
PS tmp> dir -r | select fullname

FullName
--------
C:\tmp\dir1
C:\tmp\dir2
C:\tmp\dir1\a
C:\tmp\dir1\1.txt
C:\tmp\dir1\2.txt
C:\tmp\dir1\a\1.txt
```

### 2. 絶対パスを相対パスへ変換

```powershell
PS tmp> dir -r | % { Resolve-Path -Relative $_.FullName }
（または、dir -r | Resolve-Path -Relative）

.\dir1
.\dir2
.\dir1\a
.\dir1\1.txt
.\dir1\2.txt
.\dir1\a\1.tx
```
