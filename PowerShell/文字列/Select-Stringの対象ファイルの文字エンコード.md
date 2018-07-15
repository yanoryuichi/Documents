# Select-Stringの対象ファイルの文字エンコード

## 前提

以下のようにSJIS/UTF16/UTF8（BOMなし）/UTF8（BOMあり）のファイルがあったとする。

```powershell
sjis.txt
utf16.txt
utf8-bom.txt
utf8-nobom.txt
```

## 各文字エンコードの指定

### UTF8とUTF16を検索（デフォルト）

```powershell
PS> sls "日本語" *.txt
utf16.txt:1:日本語
utf8-bom.txt:1:日本語
utf8-nobom.txt:1:日本語
```

- Encodingオプションなしの、デフォルトでは、UTF8（BOMあり、なし共に）とUTF16（UTF16には必ずBOMが必要）がマッチする。

### SJISを検索

```powershell
PS> sls "日本語" *.txt -Encoding default
sjis.txt:1:日本語
utf16.txt:1:日本語
utf8-bom.txt:1:日本語
```

- Encodingオプションにdefaultを指定すると、日本語Windowsの既定であるSJISとUTF8（BOMあり）とUTF16がマッチする。
- エクスプローラーのWindows Searchで検索する場合と同じ動作。

### BOMありのUTF8とUTF16を検索

```powershell
PS> sls "日本語" *.txt -Encoding unicode
utf16.txt:1:日本語
utf8-bom.txt:1:日本語
```

- Encodingオプションにunicodeを指定すると、UTF8（BOMありのみ）とUTF16がマッチする。
- まり使わないかも？


## 参考

- https://technet.microsoft.com/ja-JP/library/dd315403.aspx
