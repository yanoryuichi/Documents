# Radeonのグラフィックカードでカスタム解像度を設定

http://radeon.pcdiyweb.net/?Faq#n07140ffより以下引用。

1. Catalyst Control Centerを開き、Information Center→Graphics Software→2D Driver File Pathの内容を確認する。
2. レジストリエディタでHKEY_LOCAL_MACHINE以下前項で確認したキーを開き、 
3. + Catalyst Control Centerを開き、Information  Center→Graphics Software→2D Driver File Pathの内容を確認する。 
4. ++ DALNonStandardModesBCDに追加したい解像度を8byte単位で列挙する。
5. + レジストリエディタでHKEY_LOCAL_MACHINE以下前項で確認したキーを開き、

そこにDALNonStandardModesBCDと言う名前でバイナリ値を作成する。

1. + DALNonStandardModesBCDに追加したい解像度を8byte単位で列挙する。

その内容は水平解像度・垂直解像度・色深度・リフレッシュレートの値を各々2byteでBCD表記したものであり、
この内色深度とリフレッシュレートは0で省略可能。例として、1400x1050と1360x1024の解像度を追加する場合は下記の通り。 

```powershell
14 00 10 50 00  0 00 00 13 60 10 24 00 00 00 00
```

## 参考
http://radeon.pcdiyweb.net/?Faq#n07140ff
