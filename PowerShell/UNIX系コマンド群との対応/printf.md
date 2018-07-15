# printf

```powershell
# Bash
printf "%s %d %f %x" 10.0 10 10.0 10
  => 10.0 10 10.000000 a
```

```powershell
# PowerShell
"{0:g} {1:d} {2:f} {3:x} {4:c}" -f "10.0", 10, 10.0, 10, 1000
  =>  10.0 10 10.00 a \1,000
```

```powershell
# PowerShell
(255).ToString('X')
  => FF
(19800).ToString('c')
  => \19,800
```

## 参考
http://www.dijksterhuis.org/formatting-strings-stringformat/
