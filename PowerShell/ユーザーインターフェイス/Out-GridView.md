# Out-GridView

## カスタムオブジェクトを作ってグリッドビューで表示する

```powershell
PS> $users = @()
PS> $u = New-Object psobject -Property @{ Name = "taro"; Age = 19 }
PS> $users += $u
PS> $u = New-Object psobject -Property @{ Name = "jiro"; Age = 15 }
PS> $users += $u
PS> $users | Out-GridView
```
