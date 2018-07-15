# Select-Objectでリスト操作

## 先頭からN行だけ選択

```powershell
ps | select -First 2
```

- UNIX Shellの head -2 相当

## 末尾からN行だけ選択

```powershell
dir *.txt | select -Last 2
```

- UNIX Shellの tail -2 相当

## 先頭からN行スキップしてそれ以降を選択

```powershell
gc test.txt | select -Skip 2
```

- 1,2行目をスキップして、3行目以降を選択
- UNIX Shellの tail -n +3 相当

## 参考

- https://technet.microsoft.com/en-us/library/ee176955.aspx
- https://ss64.com/ps/select-object.html
