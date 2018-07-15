# オブジェクトのプロパティの選択 - Select-Object

## 前提

```powershell
PS C:\Users\taro\tmp> dir
 
Mode           LastWriteTime       Length Name
----           -------------       ------ ----
-a---    2012/05/05    14:04            3 1.txt
-a---    2012/05/05    14:04            3 2.txt
-a---    2012/05/05    14:04            3 3.txt
```

## 特定のプロパティを選択

```powershell
PS C:\Users\taro\tmp> dir | Select-Object Name

Name
----
1.txt
2.txt
3.txt
```

## 先頭（末尾）のプロパティを選択

```powershell
PS C:\Users\taro\tmp> dir | Select-Object -first 2

Mode           LastWriteTime       Length Name
----           -------------       ------ ----
-a---    2012/05/05    14:04            3 1.txt
-a---    2012/05/05    14:04            3 2.txt
```

```powershell
PS C:\Users\taro\tmp> dir | Select-Object -last 1

Mode           LastWriteTime       Length Name
----           -------------       ------ ----
-a---    2012/05/05    14:04            3 3.txt
```

head/lastコマンドに相当する。

## すべてのプロパティを選択

```powershell
PS C:\Users\taro\tmp> dir | Select-Object * 

PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Users\taro\tmp\1.txt
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Users\taro\tmp
PSChildName       : 1.txt
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
ReparsePoint      :
VersionInfo       : File:             C:\Users\taro\tmp\1.txt
                    InternalName:
                    OriginalFilename:
                    FileVersion:
                    FileDescription:
                    Product:
                    ProductVersion:
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:
BaseName          : 1
Mode              : -a---
Name              : 1.txt
Length            : 3
DirectoryName     : C:\Users\taro\tmp
Directory         : C:\Users\taro\tmp
IsReadOnly        : False
Exists            : True
FullName          : C:\Users\taro\tmp\1.txt
Extension         : .txt
CreationTime      : 2012/05/03 6:38:44
CreationTimeUtc   : 2012/05/02 21:38:44
LastAccessTime    : 2012/05/05 14:04:16
LastAccessTimeUtc : 2012/05/05 5:04:16
LastWriteTime     : 2012/05/05 14:04:16
LastWriteTimeUtc  : 2012/05/05 5:04:16
Attributes        : Archive
```

## すべてのプロパティから特定のプロパティを除外

```powershell
dir | Select-Object * -exclude Mode
```

## 参考
http://technet.microsoft.com/ja-jp/library/ee176955.aspx
