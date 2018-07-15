# Select-Stringでテキスト検索

## 検索の指定方法

### ファイルのテキスト検索

```powershell
Select-String -Path "*.txt" -Pattern "hello"
```

Patternで指定する文字列はデフォルトで正規表現が使える。

### エイリアス・PathとPatternの省略

```powershell
sls "hello" *.txt
```

### OR検索

```powershell
sls "hello", "world" *.txt
```

"hello"または"world"がある行にマッチする。

### NOT検索

```powershell
sls -Path *.txt -NotMatch -Pattern "hello","world" 
```

"hello"も"world"もない行にマッチする。

### AND検索

```powershell
sls "hello" *.txt | sls "world"
または
Get-Content *.txt | Where-Object { $_ -match "hello" -and $_ -match "world" }
```

"hello"と"world"がある行にマッチする。

### -AllMatchesオプション 各行で複数の一致を検索
"hello, hello"と書かれたtest.txtがあるとする。

```powershell
PS> gc test.txt
hello, hello
```

AllMachesオプションなしでは、

```powershell
PS> $ret = sls "hello" test.txt
PS> $ret.Matches
Groups   : {hello}
Success  : True
Captures : {hello}
Index    : 0
Length   : 5
Value    : hello
```

1文字目（Index:0）のhelloだけキャプチャーされる。AllMachesオプションありでは

```powershell
PS> $ret = sls "hello" test.txt -AllMatches
Groups   : {hello}
Success  : True
 Captures : {hello}
Index    : 0
Length   : 5
Value    : hello

Groups   : {hello}
Success  : True
Captures : {hello}
Index    : 6
Length   : 5
Value    : hello
```

1文字目に加えて、5文字目（Index:6）のhelloもキャプチャーされる。

## 検索結果の加工
### マッチしたファイル名を取得

```powershell
sls "hello" *.txt | Select-Object filename | Get-Unique -AsString
```

- Select-Objectの結果はMatchInfoオブジェクトなので、Get-UniqueにはAsStringオプションを付けて文字列として解釈するようにする。


## 参考

- https://technet.microsoft.com/ja-JP/library/dd315403.aspx
