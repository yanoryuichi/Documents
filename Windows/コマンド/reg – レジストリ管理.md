# reg - レジストリ管理

## レジストリ値の設定

- https://technet.microsoft.com/en-us/library/cc742162.aspx
- http://www.atmarkit.co.jp/ait/articles/0402/21/news005.html

## レジストリ値の取得
### キーを指定して一覧取得

```powershell
reg query HKCU\Environment
```

### 値を指定して取得

```powershell
reg query HKCU\Environment /v TEMP
```

http://www.robvanderwoude.com/ntregquery.php

## レジストリの削除

```powershell
reg delete HKCU\Environment /v MY_NAME
```

- /v MY_NAMEキーの項目が削除される。

## レジストリのエクスポート

```powershell
reg export HKCU\Environment C:\tmp\env.reg
```

## reg save/restoreによるバックアップとリストア

### 参考

- http://www.atmarkit.co.jp/fwin2k/win2ktips/593regsave/regsave.html

## reg saveとreg exportの違い

- reg saveはhive形式で出力され、キーの所有権等ACLメタデータが含まれる。よって同一PC内でのバックアップに向いている。
- reg exportはテキスト形式（拡張子.reg）で出力され、メタデータは含まれない。よって、レジストリを配布するのに向いている。

## .regファイルを読み込む

- .regファイルをダブルクリックするか、
- reg import foo.reg のようにreg importを実行する。

## .regファイルの書式

- 文字コード：UTF16(リトルエンディアン）
- その他：http://www.atmarkit.co.jp/fwin2k/win2ktips/1119wrtregfil/wrtregfil.html

## 参考

- http://www.atmarkit.co.jp/ait/articles/0402/21/news005.html
- http://www.atmarkit.co.jp/fwin2k/win2ktips/391cmdreg/cmdreg.html
