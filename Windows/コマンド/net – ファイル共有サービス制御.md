# net - ファイル共有サービス制御

## サーバサイド
### 公開しているファイル共有の一覧を表示する

```powershell
net share
```

### 公開しているファイル共有の詳細を表示する

```powershell
net share my-share
```

### ファイル共有を公開する1

```powershell
net share my-share=C:\Users\taro\pub01 /grant:everyone,full
```

### ファイル共有を公開する2

```powershell
net share my-private=C:\Users\taro\pub01 /grant:mypc\taro,full /grant:everyone,read
```

サーバがドメイン環境な場合、"ドメイン名\ユーザ名"でユーザを指定する。

### 公開しているファイル共有を削除する

```powershell
net share my-share /delete
```

### 公開しているファイル共有の設定を変更する
ファイル共有を削除した後、作り直す。（多分、この方法しかない？）

### （共有させる）ファイル・フォルダのアクセス権の設定

```powershell
icacls C:\Users\taro\pub01                    #(1) ACLの確認
icacls C:\Users\taro\pub01 /grant hanako:f /t #(2) hanakoにpub01以下全ファイルのフルコントロールを許可
```

- icacls(cacls)についてはhttp://www.atmarkit.co.jp/fwin2k/win2ktips/718edtcacls/edtcacls.htmlを参照する。

### アクセス制御について

- ファイル・フォルダのアクセス権とファイル共有のアクセス権は別のもの。
- ファイル共有のアクセス権でeveryoneをフルコントロールして、ファイル・フォルダのアクセス権でアクセス出来るユーザを絞って運用する方法もあり。

## クライアントサイド
### ネットワーク共有に接続する

```powershell
net use x: \\my-server01\my-share                        # (1)
net use x: \\my-server01\my-share /user:user01 mypass01  # (2)
net use x: \\my-server01\my-share /persistent:yes        # (3)
```

- (1) ログインしているユーザで、my-server01サーバ上のmy-share共有フォルダをXドライブにマウントする。
- (2) ユーザ名とパスワードを指定して、同上。
- (3) マシン再起動時に自動的に接続する

### 接続しているネットワーク共有一覧

```powershell
net use
```

### 接続しているネットワーク共有の削除

```powershell
net use /delete \\pc01
```

### 参考

- http://www.atmarkit.co.jp/fwin2k/win2ktips/394ipcshare/ipcshare.html

## その他
### 共有を公開しているサーバ（ホスト）の一覧
同一ワークグループ（ドメイン）：

```powershell
net view
```

ドメイン名指定：

```powershell
net view /my-domain
```

### サーバが公開している共有の一覧

```powershell
net view \\my-server01
```

IPアドレス指定：

```powershell
net view \\192.168.0.50 
```

## 参考

- http://www.atmarkit.co.jp/fwin2k/win2ktips/258netcommand/netcommand.html
