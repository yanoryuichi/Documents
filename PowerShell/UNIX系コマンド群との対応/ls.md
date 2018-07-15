# ls

## 不可視ファイルを表示

```powershell
ls -a      # Bash
dir -force # PowerShell
```

## 表示項目の指定

```powershell
ls -1              # Bash
dir -name          # PowerShell
dir | select name  # PowerShell 別の方法
```

## 絞込み検索
### ファイル名をワイルドカードで指定

```powershell
ls *.txt                      # Bash
dir *.txt                     # PowerShell
dir * -include *.txt          # PowerShell 別の方法
dir * -include *.jpg, *.gif   # PowerShell includeオプションはリストを指定出来る
```

### 除外ファイル名を指定

```powershell
ls *.txt | grep -v tmp                      # Bash
dir * -Include *.txt -Exclude *tmp*         # PowerShell
dir * -Include *.txt -Exclude *tmp*, *old*  # PowerShell excludeオプションはリストを指定できる
```
