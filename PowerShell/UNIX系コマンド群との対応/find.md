# find

## ファイル検索

```powershell
find . -name "*.txt"                  # Bash
gci -r "*.txt" | ft -a FullName,Mode  # PowerShell
```

gci(dir)コマンドレットの-Recurseオプションを使う。

### より複雑な絞込み検索をする場合

```powershell
dir -r | where { $_.Name -Like "*.txt" -and $_.LastWriteTime -gt "2013-07-01" } | ft -a FullName
```

where-objectを使う。

## find -execオプションによるコマンドの実行
### PSコマンドレットを実行する場合

```powershell
find . -name "*.txt" -exec rm {} \;  # Bash
dir -r "*.txt" | del                 # PowerShell 
```

- delのようなPSコマンドレットはパイプをつなげればその通りに実行される。
- なお、"del -whatif"のようにすると何が削除されるのが確認出来る。-whatifオプションは多くのPSコマンドレットで実装されている。

### 非PSコマンドレットを実行する場合

```powershell
find . -excc grep "ABC {}                  # Bash
dir -r | % { grep.exe "ABC" $_.fullname }  # PowerShell
```

- grep.exeのようなPSコマンドレットではないコマンドを実行する場合は、foreach（%）を使う。
- なお、PowerShellでgrepする場合は通常はSelect-Stringコマンドレットを使う。
