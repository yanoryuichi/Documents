# dirの結果を相対パスで表示

```powershell
dir -r -file *.txt | Resolve-Path -Relative
```

## 参考
http://stackoverflow.com/questions/4936522/copy-a-file-including-its-relative-path
