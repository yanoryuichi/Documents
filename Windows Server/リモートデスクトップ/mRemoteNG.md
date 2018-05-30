# mRemoteNG

## 特徴

- Windowsの標準RDPクライアントソフトをHi DPI環境で使うと、接続元のOSと接続先のOSの組み合わせ次第で、DPIスケーリングが正常に動作しない。
- 基本的にリモートデスクトップにおいては接続先のDPIスケーリングを変更することが出来ない。
- mRemoteNGを使と、接続先のOSはDPI仮想化されて全体がぼやけるが、DPIは接続元のOSと連動する。
- 接続元のOSがDPIスケーリング150%以上などのHi DPI環境では接続先のOSが100%だとほとんど視認できないくらい小さく見えるはずなので、DPI仮想化が起きてもmRemoteNGを使った方がマシと言える。

## インストール

- 以下のURLにアクセスする。
  - https://mremoteng.org/
- MSIインストーラーをダウンロードして、インストールする。

インストール先

```clike
C:\Program Files (x86)\mRemoteNG
```

レジストリ

```clike
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\mRemoteNG
HKEY_CURRENT_USER\Software\mRemoteNG
```

設定ファイル

```clike
C:\Users\USERNAME\AppData\Roaming\mRemoteNG
C:\Users\USERNAME\AppData\Local\mRemoteNG
```


## 参考

- https://mremoteng.org/
- https://www.howtogeek.com/171472/how-to-use-mremoteng-to-manage-all-your-remote-connections/
