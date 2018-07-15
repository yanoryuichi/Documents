# cut

## 前提

```powershell
> echo-program.exe(またはecho-program.sh)
ABC DEF XYZ
123 456 789
FOO BAR BAZ
```

上のような実行すると文字列を出力するプログラムがあるとする。

## ConvertFrom-Csvコマンドレット

```powershell
echo-program.sh | cut -d " " -d 1,3                                                # Bash
echo-program.exe | ConvertFrom-Csv -Delimiter " " -Header (1..3) | select "1", "3" # PowerShell
```

PowerShellで出力結果を整形するにはft -a等を使う。

## デリミタの指定を正規表現で行いたい場合

```powershell
echo-program.sh  | awk 'BEGIN{FS=" +"}{print $1,":",$3}'  # Bash
echo-program.exe | % { ($_ -split "\s+")[0,2] -join ":" } # PowerShell
```

- %(Foreach-Object)でループ処理し、$_を-splitする際に"\s+"で正規表現を使う。
- -splitの結果は配列なので、必要なデータだけスライスして取り出す。

## 参考

- http://technet.microsoft.com/en-us/library/hh849890.aspx
