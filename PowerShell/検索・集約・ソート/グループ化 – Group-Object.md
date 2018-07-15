# グループ化 - Group-Object

## 前提

```powershell
gci | select name, extension | ft -auto
```

```powershell
Name  Extension
----  ---------
1.txt .txt
2.txt .txt
3.txt .txt
4.csv .csv
5.csv .csv
6.doc .doc
```

## 拡張子でグループ化

```powershell
gci | group-object extension | ft -auto
```

```powershell
Count Name Group
----- ---- -----
    3 .txt {1.txt, 2.txt, 3.txt}
    2 .csv {4.csv, 5.csv}
    1 .doc {6.doc}
```
