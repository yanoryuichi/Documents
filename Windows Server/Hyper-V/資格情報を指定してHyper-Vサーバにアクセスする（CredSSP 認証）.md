# 資格情報を指定してHyper-Vサーバにアクセスする（CredSSP 認証）

- Windows リモート管理 (WinRM) サービスでリモート クライアントからの CredSSP 認証を受け付けるように設定することで、クライアントPCのHyper-Vマネージャから、HyperVサーバへ接続できるようになる。
- なお、ドメイン環境の場合、自分の資格情報（クライアントPCにログインしているユーザの資格情報）ならKerberos認証がデフォルトで可能なはず。

## Hyper-Vサーバ側

### 確認

```clike
PS C:\> Get-WSManCredSSP
このコンピューターは、新しい資格情報の委任を許可するようには構成されていません。 
このコンピューターは、リモート クライアント コンピューターから資格情報を受け取るように構成されていません。
```

### 有効化

```clike
PS C:\> Enable-WSManCredSSP -Role Server
```

## クライアントPC側

- スタートメニューからサービスを起動する。（WIN+Rから、services.mscを実行）
- Windows Remote Management (WS-Management) を開始する。

```clike
PS C:\> winrm quickconfig
```
