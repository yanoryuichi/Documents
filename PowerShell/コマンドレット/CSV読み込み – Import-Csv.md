# CSV読み込み - Import-Csv

## ヘッダ指定

```powershell
Import-Csv .\users.csv -Header 'NAME', 'AGE', 'SEX', 'BIRTHDAY' | Select-Object NAME, SEX  
```

デフォルト（オプション指定なし）ではCSVファイルの1行目がヘッダとして扱われる。
### ヘッダにシリアルナンバーを指定

```powershell
Import-Csv .\users.csv -Header (1..4) | Select-Object "1", "3"
```

selectする際は"1"のように引用符で包んで指定する。

## 区切り文字指定

```powershell
Import-Csv -Delimiter "`t" .\users.tsv 
```

タブ区切りの場合。

## カラムの型を指定

```powershell
Import-Csv .\users.csv | Sort-Object { [datetime]$_.BIRTHDAY } 
```

あるいは、sortの後にパイプでつなげる事を考慮すると、下のようにキャストして変数を再設定する。

```powershell
Import-Csv .\users.csv | foreach { $_.BIRTHDAY = $_.BIRTHDAY -as [datetime]; $_ } | sort BIRTHDAY
```

なお、datetime型のカラムのフォーマットは、"2000/4/1"や"2000-04-01"や"2000/04/01 12:59:59"等が認識されて、1つのファイルの中に混在していても良い。

## SJISのCSVファイルを読み込む

```powershell
Import-Csv .\users.csv -Encoding Default 
```

- オプション指定なしではUnicodeが想定される。
- DefaultがSJISなのは、多分日本語版Windowsのコードページ設定がSJISだからだと思われる。

## パイプからCSVを読み込む

```powershell
Get-Content .\users.csv | ConvertFrom-Csv | Select NAME, SEX
```

ConvetFrom-CSVコマンドレットを使う。
### ヒアドキュメントを使って

```powershell
ConvertFrom-Csv -Header date, time, status,user,ip  @"
05/25/2010,18:48:33,Stop,a1usak,10.128.212.212
05/25/2010,18:48:36,Start,q2uhal,10.136.198.231
05/25/2010,18:48:09,Stop,s0upxb,10.136.198.231
"@
```

### クリップボードを使って

```powershell
Get-Clipboard | ConvertFrom-Csv -Delimiter " " -Header (1) | select "1"
```
