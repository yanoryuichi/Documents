# regexp - 正規表現

## メソッドの構成

```clike
Find(All)?(String)?(Submatch)?(Index)?
```

## 複数行 - mフラグ

```clike
text := ` abc1
 xyz2`
re := regexp.MustCompile(`(?m)^ (.+)$`)
text = re.ReplaceAllString(text, "[$1]")
fmt.Println("DEBUG:" + text)
```

```clike
DEBUG:[abc1]
[xyz2]
```

## 参考

- http://golang.org/pkg/regexp/
- http://swtch.com/~rsc/regexp/regexp3.html
