# tasklist - プロセス一覧表示

## 全プロセス一覧

```powershell
tasklist
```

## 絞込み検索
### ユーザ名で調べる

```powershell
tasklist /fi "username eq taro"
```

### イメージ名（アプリケーション名）で調べる

```powershell
tasklist /fi "imagename eq iexplore.exe"
```

### プロセスIDで調べる

```powershell
tasklist /fi "PID eq 1234"
```

|フィルタ名|演算子|値|
|-|-|-|
|STATUS|eq　ne|RUNNING（実行中）または|
|||NOT RESPONDING（応答なし）|
|IMAGENAME|eq　ne|イメージ名|
|PID|eq　ne　gt　lt　ge　le|プロセスID|
|SESSION|eq　ne　gt　lt　ge　le|セッション番号|
|SESSIONNAME|eq　ne|セッション名|
|CPUTIME|eq　ne　gt　lt　ge　le|CPU使用時間（hh:mm:ss）|
|MEMUSAGE|eq　ne　gt　lt　ge　le|メモリ使用量（KB）|
|USERNAME|eq　ne|ユーザー名|
|SERVICES|eq　ne|サービス名|
|WINDOWTITLE|eq　ne|ウィンドウのタイトル|
|MODULES|eq　ne|DLL名|

## フォーマット指定
### LIST

```powershell
TASKLIST /V /FO LIST
```

```powershell
イメージ名:          tasklist.exe
PID:                 4316
セッション名:        Console
セッション#:         1
メモリ使用量:        8,916 K
状態:                Unknown
ユーザー名:          MYPC01\taro
CPU 時間:            0:00:00
ウィンドウ タイトル: N/A
```

### CSV

```powershell
TASKLIST /V /FO CSV > process-list.csv
```

## 参考
http://technet.microsoft.com/ja-jp/library/cc730909(v=WS.10).aspx
