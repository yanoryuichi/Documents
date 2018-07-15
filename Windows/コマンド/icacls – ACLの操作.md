# icacls - ACLの操作

## ユーザのアクセス権（ACE）を設定する

```powershell
icacls file1.txt /grant everyone:(F)
```

### ACEを上書き設定する

```powershell
icacls file1.txt /grant:r everyone:(F)
```

## ディレクトリに継承を設定する1

```powershell
icacls dir1 /grant everyone:(OI)(CI)(F)
```

- dir1にeveryoneのACEが設定される。

## ディレクトリに継承を設定する2

```powershell
icacls dir1 /grant everyone:(OI)(CI)(IO)(F)
```

- dir1には設定されず、dir1以下のファイルとディレクトリにeveryoneのACEが設定される。
- http://superuser.com/questions/95950/what-windows-permissions-should-be-set-to-protect-a-directory-while-allowing-it/731102#731102

## ユーザのアクセス権（ACE）を削除する

```powershell
icacls file1.txt /remove everyone
```

http://www.atmarkit.co.jp/fwin2k/win2ktips/1339rmacl/rmacl.html

## アクセス権をリセットして親フォルダから継承のみの状態にする

```powershell
icacls dir1 /reset /t
```

http://www.atmarkit.co.jp/fwin2k/win2ktips/1325aclreset/aclreset.html

## 設定例
### everyoneに対してアクセス権変更を許可する

```powershell
icacls dir1 /grant everyone:(M)
```

### everyoneの書き込みを禁止する

```powershell
icacls dir1 /deny everyone:(CI)(OI)(F)
icacls dir1 /deny everyone:(CI)(OI)(W)
```

### everyoneに対してdir1フォルダ以下のファイルやフォルダのアクセス権変更を許可するが、dir1フォルダ自体はリードオンリーにする

```powershell
icacls dir1 /grant everyone:(OI)(CI)(IO)(M)
icacls dir1 /grant everyone:(R)
```

### everyoneに対してdir1フォルダ以下にファイルやフォルダを作る事は許可するが、削除する事は許可しない

```powershell
icacls dir1 /grant everyone:(OI)(CI)(WD)(RD)
icacls dir1 /grant everoyne:(IO)(AD)
```

"(AD)"はファイルを修正する事を許可する。

## 参考

- http://technet.microsoft.com/en-us/library/cc753525%28WS.10%29.aspx
- http://searchwindowsserver.techtarget.com/tip/Icacls-syntax-basics-Automating-Windows-file-permissions

### ACL概要
http://www.atmarkit.co.jp/fwin2k/win2ktips/700whatisacl/whatisacl.html
