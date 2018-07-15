# grep

## テキストファイルの中の文字列を検索する場合
### Select-Stringコマンドレット

```powershell
grep taro user.txt           # Bash
Select-String taro user.txt  # PowerShell
sls taro user.txt            # PowerShell
```

### find -exec grep(あるいはfind | xargs grep)のように再帰的に検索する場合

```powershell
find . -name "*.txt" -exec grep "hello"  # Bash
dir -r *.txt | sls hello                 # PowerShell
```

dir(Get-ChildItem)の-Filterオプションの詳細については別ページを参照の事。

### 検索出来る文字コード

```powershell
sls "こんにちは" utf8.txt,utf8n.txt,utf16le.txt,sjis.txt

utf8.txt:1:こんにちは
utf8n.txt:1:こんにちは
utf16le.txt:1:こんにちは
```

- UTF8（BOM有り無し共）、UTF16LEは対象になる。
- SJISは対象にならない。

### SJISを検索する場合

```powershell
sls -encoding default "こんにちは" utf8.txt,utf8n.txt,utf16le.txt,sjis.txt

utf8.txt:1:こんにちは
utf16le.txt:1:こんにちは
sjis.txt:1:こんにちは
```

- SJIS、UTF8（BOM有り）、UTF16LEは対象になる。
- UTF8（BOM無し）は対象にならない。

### UNIX系OSと相互運用は？

- UNIX系OSと相互運用する事を考えるとUTF8（BOM無し）が無難に思える。
- が、それ以外の文字コードのファイルも混じる状況なら、Select-Stringは諦めて、マルチ文字コード対応な外部コマンドを使う方が良いかもしれない。
  - jvgrep等は使いやすい。https://github.com/mattn/jvgrep/releases


### 参考

- [[Select-String>http://yanor.net/wiki/?PowerShell%2F%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%83%AC%E3%83%83%E3%83%88%2F%E6%96%87%E5%AD%97%E5%88%97%E3%83%BB%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E3%83%86%E3%82%AD%E3%82%B9%E3%83%88%E6%A4%9C%E7%B4%A2%20-%20%20Select-String]]

### Find-String コマンドレット （高機能なSelect-String）

- カラー出力される。
- https://github.com/drmohundro/Find-String

## PSコマンドレットの出力を検索する場合
### where-objectコマンドレット

```powershell
ls | grep ".txt"                # Bash
dir | where Name -Like "*.txt"  # PowerShell
```

```powershell
dir | ? { $_.LastWriteTime -gt "2013-07-01" -and $_.LastWriteTime -lt "2013-07-31" }
```

where-objectについて詳しくは別ページを参照の事。

## PSコマンドレット以外の出力を検索する場合

```powershell
netstat -n | Out-String -Stream | sls "192.168."
```
