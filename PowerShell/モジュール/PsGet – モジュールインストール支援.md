# PsGet - モジュールインストール支援

## 公式
http://psget.net/

## PsGetのインストール

```powershell
PS> (new-object Net.WebClient).DownloadString("http://psget.net/GetPsGet.ps1") | iex
```

## PsGetを使ってモジュールをインストール

```powershell
PS> Install-Module Find-String
```
