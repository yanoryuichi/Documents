# ConvetFrom-String 複数行文字列をコレクションオブジェクトへ変換

### 複数行文字列を用意する

```powershell
PS> "taro,18","hanako,15"
taro,18
hanako,15
```

- ここではカンマ区切りを想定する。

### ConvertFrom-Stringコマンドレットでコレクションオブジェクトへ変換する

```powershell
PS> "taro,18","hanako,15" | ConvertFrom-String -Delimiter "," -PropertyNames "name", "age"
name   age
----   ---
taro    18
hanako  15
```

- -PropertyNamesを指定しなければ、自動的にP1,P2,P3,のようなキー名が設定される。

```powershell
PS> $data = "taro,18","hanako,15" | ConvertFrom-String -Delimiter "," -PropertyNames "name", "age"
PS> $data | ConvertTo-Json
[
    {
        "name":  "taro",
        "age":  18
    },
    {
        "name":  "hanako",
        "age":  15
    }
]
```
