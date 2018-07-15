# netsh wlan - 無線LANプロファイル設定

## すべてのワイヤレスプロファイルを表示する

```powershell
netsh wlan show profiles
```

## プロファイル（SSID）の詳細を表示する

```powershell
netsh wlan show profiles name=MySSID 
```

### セキュリティキーを表示する

```powershell
netsh wlan show profiles name=MySSID key=clear
```

## ワイヤレスプロファイルを削除する

```powershell
netsh wlan delete profile name=MySSID
```

## プロファイルのエクスポート

```powershell
netsh wlan export profile
```

直下に"インターフェイス名-プロファイル名.xml"（例えばWi-Fi-MySSID.xml）というファイルが作成される。

## プロファイルのインポート

```powershell
netsh wlan add profile filename="Wi-Fi-MySSID.xml
```

## プロファイル名の変更

- netsh wlan set profileparameter では出来ないようだ。
- よって、プロファイルをエクスポートして、テキストエディタで書き替えて、インポートする。

## 参考

- http://windows.microsoft.com/ja-JP/windows-8/manage-wireless-network-profiles
- https://technet.microsoft.com/ja-jp/library/cc755301(v=ws.10).aspx
- https://community.spiceworks.com/how_to/24989-export-import-wireless-network-info-on-windows-machines
