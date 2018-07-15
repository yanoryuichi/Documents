# w32tm

以下のコマンドは管理者権限で実行する。

## NTPクライアントとしての時刻同期の状態を確認

```powershell
w32tm /query /status 
```

上のコマンドの結果表示される「ソース」がNTPサーバ（もしくは内蔵時計）を示す。
### ソースだけ確認

```powershell
w32tm /query /source
```

## NTPサーバを変更する

```powershell
w32tm /config /update /syncfromflags:manual /manualpeerlist:ntp.nict.jp
```

上のコマンドでNTPサーバはntp.nict.jpになる。

## 時刻同期をその場で行う

```powershell
w32tm /resync
```

上のコマンドを実行しても直ちにNTPクライアント（ローカルのPC）の時刻が変更されるわけではない。徐々に調整される。時刻調整の状況は以下の/stripchartオプションで確認する。

## NTPサーバとの時間差を表示する

```powershell
w32tm /stripchart /computer:ntp.nict.jp
```

## ドメイン環境（ActiveDirectory）での時刻同期

- ドメイン環境ではドメインメンバーのPCはドメインコントローラーのサーバをNTPサーバとする。
- 従って、ドメイン環境でのPCの時刻変更はドメインコントローラーに対して行う必要がある。

## Hyper-V環境での時刻同期のソース
Hyper-V環境でのゲストOSのソースは以下のようになる。ゲストOSの時刻を変更するにはホストOSのソースを変更する。

```powershell
C:\Windows\system32>w32tm /query /source
VM IC Time Synchronization Provider
```

## 参考
http://www.atmarkit.co.jp/fwin2k/operation/winntp203/winntp203_03.html
