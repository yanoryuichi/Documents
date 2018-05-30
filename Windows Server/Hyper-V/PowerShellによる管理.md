# PowerShellによる管理

## 仮想マシン一覧取得

```clike
Get-WmiObject -Namespace root\virtualization -ComputerName "." -Class Msvm_Computersystem |
  Select-Object ElementName,StatusDescriptions
```

リモートのHyper-Vサーバを参照する場合は -ComputerName "windows-server-01" のように指定する。

## 参考

- http://blogs.gine.jp/kusa/archives/76
