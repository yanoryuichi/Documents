# PDFファイルのインデックス

## Windows 8でPDFファイルのインデックスが出来ない

- Windows 8では標準でPDFファイルのインデックスが可能だが、Adobe Readerをインストールすると、その設定が壊れる。
- コントロールパネル→[インデックスのオプション]→[詳細オプション]で、[ファイルの種類]の.pdfが"登録されているifilterが見つかりません”となる。
- これを解決するには、以下のAdobeのページにあるように、HKEY_CLASSES_ROOT\.pdf\PersistentHandler を {1AA9BF05-9A97-48c1-BA28-D9DCE795E93C} にする。
  - https://helpx.adobe.com/acrobat/kb/pdf-search-breaks-110-install.html

### 参考
http://superuser.com/questions/507575/indexing-pdfs-in-windows-8/508235#508235

## 64ビット版Windows 7でPDFのインデックス化を可能にする

http://news.mynavi.jp/articles/2010/06/22/w7/002.html
