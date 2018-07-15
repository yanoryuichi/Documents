# Copy-ItemのRecusiveオプション

## 概要

- PowerShellのCopy-Itemを-Recursiveなしでディレクトリに対して実行すると、そのディレクトリだけがコピーされる。
- コピー先ディレクトリが存在しない場合はコピー元ディレクトリと同名で新規にディレクトリが作成され、
- コピー先ディレクトリが存在する場合はコピー先ディレクトリ下にコピー元ディレクトリと同名で新規にディレクトリが作成される。
- なお、UNIXのBashなどの場合、cpを-rなしでディレクトリに対して実行するとエラーになる。

## ディレクトリだけコピーする - Recusiveオプションなし
### 0. 現在の状態

```powershell
PS> dir -r | select fullname

FullName
--------
C:\tmp\dir1
C:\tmp\dir1\1.txt
```

### 1. dir1をコピーしてdir2を作る

```powershell
PS> Copy-Item dir1 dir2
PS> dir -r | select fullname

FullName
--------
C:\tmp\dir1
C:\tmp\dir2
C:\tmp\dir1\1.txt
```

### 2. dir1をコピーしてdir2の下にdir1を作る

```powershell
PS> Copy-Item dir1 dir2
PS> dir -r | select fullname

FullName
--------
C:\tmp\dir1
C:\tmp\dir2
C:\tmp\dir1\1.txt
C:\tmp\dir2\dir1
```

## ディレクトリを再起的にコピーする - Recusiveオプションあり
### 0. 現在の状態

```powershell
PS> dir -r | select fullname

FullName
--------
C:\tmp\dir1
C:\tmp\dir1\1.txt
```

### 1. dir1をコピーしてdir2を作る

```powershell
PS tmp> Copy-Item -Recurse dir1 dir2
PS tmp> dir -Recurse | select fullname

FullName
--------
C:\tmp\dir1
C:\tmp\dir2
C:\tmp\dir1\1.txt
C:\tmp\dir2\1.txt
```
