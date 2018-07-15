# エイリアス - Get-Alias他

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

## エイリアスにオプション付きのコマンドレットを指定する

```powershell
Remove-Item alias:ls
function ls() {
  gci $args | fw -column 4
}
```

- PowerShellのエイリアスはコマンドレットにオプションを指定出来ないので（Set-Alias ls "gci -r"みたいなのは出来ない）、ファンクションを使う。
- エイリアスはファンクションに優先するので、すでにエイリアスがある場合は削除してから、ファンクションを作成する。


## 参考

- Get－Alias http://technet.microsoft.com/ja-jp/library/ee176839.aspx
- Set-Alias http://technet.microsoft.com/ja-jp/library/ee176958.aspx
- http://huddledmasses.org/powershell-power-user-tips-bash-style-alias-command/
