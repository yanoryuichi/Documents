# PowerShell上でsvnadminを使う

- svnadminはloadやdumpでダンプファイルの入出力をリダイレクト（>と<）で行う。
- PowerShellはリダイレクトの際に入出力データをテキスト（UTF16など）への変換を試みる。
- 従って、PowerShellでsvnadminをそのまま使うと問題が起きやすい。
- CMDを呼び出して、その中でsvnadmnを実行する方が無難。

### svnadmin dump

```bash
PS> cmd /c svnadmin.exe dump "C:\svn\repos" `> svn.repos.dump
```

### svnadmin load

```bash
PS> cmd /c "svnadmin.exe load new_repos < svn.repos.dump"
```
