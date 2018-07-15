# sc - サービスプログラム制御

## サービスの状態確認

```powershell
sc.exe query foo-service
```

## サービス一覧

```powershell
sc query state= all | findstr SERVICE_NAME
```

## サービスの開始

```powershell
sc start foo-service
```

## スタートアップの種類を変更

```powershell
sc config foo-service start= auto
sc config foo-service start= disabled
```

## サービスの削除

```powershell
sc.exe delete foo-service
```

## サービスの登録

- nssmやrunasserviceを使う。
- http://stackoverflow.com/questions/415409/run-batch-file-as-a-windows-service/13294293#13294293
- http://serverfault.com/questions/54676/how-to-create-a-service-running-a-bat-file-on-windows-2008-server

## 参考
http://www.itmedia.co.jp/enterprise/articles/0809/17/news065.html
