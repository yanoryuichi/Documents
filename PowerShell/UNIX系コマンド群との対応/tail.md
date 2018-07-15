# tail

## tail

```powershell
ps | tail -3                  # Bash
Get-Process | select -Last 3  # PowerShell
```

## tail -f

```powershell
tail -f access.log            # Bash
gc -Wait -Tail 10 access.log  # PowerShell
```

Get-Contentsコマンドレットの-Waitオプションを使う。
