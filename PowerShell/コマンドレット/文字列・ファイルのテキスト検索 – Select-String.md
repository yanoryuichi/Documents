# 文字列・ファイルのテキスト検索 - Select-String

## ファイルのテキスト検索

```powershell
Select-String -Path "*.txt" -Pattern "hello"
```

Patternで指定する文字列はデフォルトで正規表現が使える。

## dirコマンドレットと組み合わせて再帰的に

```powershell
dir -Recurse -Filter "*.txt" | Select-String "hello"
```

## OR検索

```powershell
Select-String -Path "*.txt" -Pattern "hello","world"
```

"hello"または"world"がある行にマッチする。

## NOT検索

```powershell
Select-String -Path "*.txt" -NotMatch -Pattern "hello","world"
```

"hello"も"world"もない行にマッチする。

## AND検索

```powershell
Select-String "hello" *.txt | Select-String "world"
または
Get-Content *.txt | Where-Object { $_ -match "hello" -and $_ -match "world" }
```

"hello"と"world"がある行にマッチする。

## マッチしたファイル名を取得

```powershell
Select-String -Path "*.txt" -Pattern "hello" | Select-Object filename | Get-Unique -AsString
```

## PowerShell非対応の出力結果を検索する

```powershell
dir | Out-String -Stream | Select-String txt
```

Out-Stringを介してやる。

## エイリアス

```powershell
netstat -n | Select-String ":80"
netstat -n | sls ":80"
```

## 参考

- http://blogs.technet.com/b/heyscriptingguy/archive/2011/08/04/use-an-easy-powershell-command-to-search-files-for-information.aspx
- [[PowerShell/モジュール/Find-String - grepやackのようなもの]]
