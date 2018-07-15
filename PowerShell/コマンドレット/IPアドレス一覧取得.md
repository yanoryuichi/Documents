# IPアドレス一覧取得

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | select Description, IPAddress
```
