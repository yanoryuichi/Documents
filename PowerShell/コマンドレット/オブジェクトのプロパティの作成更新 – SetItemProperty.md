# オブジェクトのプロパティの作成更新 - SetItemProperty

## ドットから始まるファイル・ディレクトリに不可視属性を設定

```powershell
gci -Recurse -Filter '.*' | Set-ItemProperty -name Attributes -value "Hidden"
```

## 参考
http://technet.microsoft.com/ja-jp/library/dd315383.aspx
