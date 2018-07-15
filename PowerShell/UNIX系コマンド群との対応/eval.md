# eval

Invoke-Expressionを使う。

```powershell
PS> $str="date"
PS> Invoke-Expression $str
2014年11月28日 10:39:14
```

```powershell
PS> Invoke-Expression $(echo "date")
2014年11月28日 10:38:41
```

## 参考

- http://technet.microsoft.com/ja-JP/library/dd347550.aspx
