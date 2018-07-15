# エイリアス Set-Alias Get-Alias他

## コマンドレットのエイリアス作成

```powershell
Set-Alias myls Get-ChildItem
```

### オプション付きのコマンドレットのエイリアスを作成

```powershell
Remove-Item alias:ls
function ls() {
  gci $args | fw -column 4
}
```

- PowerShellのエイリアスはコマンドレットにオプションを指定出来ないので（Set-Alias ls "gci -r"みたいなのは出来ない）、ファンクションを使う。
- エイリアスはファンクションに優先するので、すでにエイリアスがある場合は削除してから、ファンクションを作成する。

### 実行ファイル（EXE）のエイリアスを作成

```powershell
Set-Alias mynotepad ("notepad.exe")
Set-Alias mychrome ("C:\Program Files (x86)\Google\Chrome\Application\chrome.exe")
```

- PATHに通ってないEXEならフルパスで指定する
- 引用符""でくくるのでパス名にスペースを含んでもOK

### オプション付きの実行ファイル（EXE）のエイリアスを作成

```powershell
function mychrome() {
    Start-Process "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" -ArgumentList "--incognito"
}
```

- Start-Processで外部プロセスを実行し、その際に-ArgumentListでオプション（コマンド引数）を指定する

### 環境変数を展開してオプション付きの実行ファイル（EXE）のエイリアスを作成

```powershell
function mychrome() {
   $x = "--user-data-dir=`"" + $env:USERPROFILE + "\my chrome profile`""
   $args += $x
   Start-Process "c:\Program Files (x86)\Google\Chrome\Application\chrome.exe" -ArgumentList $args
}
```

- PowerShell内で変数$xにオプション文字列を格納する
- この時、値であるディレクトリパスにスペースが含まれることを想定して引用符""でくるむが、このままではPowerShell内でそれが展開されてしまうので`（バッククォート）でエスケープする
- できた$xを$args配列にpushする
- -ArgumentListに$argsを指定する

## エイリアス元のコマンドレットを探す

```powershell

Get-Alias dir                                    
> CommandType     Name                                               ModuleName  
> -----------     ----                                               ----------  
> Alias           dir -> Get-ChildItem                                           
```

## あるコマンドレットのエイリアス名を探す

```powershell
Get-Alias -Definition Get-ChildItem* 
> Get-Alias -Name Get-ChildItem*       
> Get-Alias -Name Get-ChildItem*       
> Get-Alias -Definition Get-ChildItem*
```

## エイリアスを削除する

```powershell
Remove-Item alias:ls
```



## 参考

- Get－Alias http://technet.microsoft.com/ja-jp/library/ee176839.aspx
- Set-Alias http://technet.microsoft.com/ja-jp/library/ee176958.aspx
- Start-Process https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/start-process?view=powershell-5.1
- http://huddledmasses.org/powershell-power-user-tips-bash-style-alias-command/
