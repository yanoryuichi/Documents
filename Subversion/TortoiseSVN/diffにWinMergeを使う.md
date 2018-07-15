# diffにWinMergeを使う

"Settings" -> "Diff viewer"で以下のように指定する。

```bash
C:\Program Files (x86)\WinMerge\WinMergeU.exe -e -ub -dl %bname -dr %yname %base %mine
```

## 参考
http://tortoisesvn.net/docs/nightly/TortoiseSVN_ja/tsvn-dug-settings.html
