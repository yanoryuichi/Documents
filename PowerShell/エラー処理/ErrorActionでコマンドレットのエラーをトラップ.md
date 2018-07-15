# ErrorActionでコマンドレットのエラーをトラップ

## 前提

- コマンドレットの実行失敗などで発生するエラーのエラーオブジェクトは$error配列に格納される。（$error[0]が直近）
- エラーには、終了して例外を投げるエラーと、終了しないで続行するエラーがある。
- コマンドレットのエラーは、デフォルトでは終了しないで続行するので、例外を補足出来ない。
- デフォルトのエラーの動作を変えるには、シェルで$ErrorActionPreference変数を指定するか、コマンドレット実行時に-ErrorActionパラメータを付与する。
- 従って、状況によるが、PSスクリプト内では、$ErrorActionPreference = "Continue"で通常のコマンドレットの失敗は処理を続行し、失敗すると致命的と思われるコマンドレットはFoo-Bar -ErrorAction = "Stop"で実行し、それによる例外をtry/catch/finallyで補足し、ログを書いてExitするなどの適切な例外処理を作るのが良い。

## 存在しないフォルダへcdを実行する時の例外処理

```powershell
$ErrorActionPreference = "Continue"
try {
    cd c:\tmp123
} catch {
    write-host "1) " $error[0]
}

try {
    cd c:\tmp456 -ErrorAction "Stop"
} catch {
    write-host "2) " $error[0]
}
```


↓

```powershell
cd : パス 'C:\tmp123' が存在しないため検出できません。
発生場所 C:\Users\brazil\tmp\1.ps1:3 文字:6
+      cd c:\tmp123
+      ~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (C:\tmp123:String) [Set-Location], ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.SetLocationCommand

2)  パス 'C:\tmp456' が存在しないため検出できません。
```



- 1)のエラーは例外が補足されていない。（エラーメッセージはそのままコンソールに出力される）
- 2)のエラーは例外が細くされ、エラーメッセージが処理されている。


## 実行可能か調べる（パスが通っているか調べる）

```powershell
if ((Get-Command "no-such-app.exe" -ErrorAction SilentlyContinue) -eq $Null) {
  echo "The app is not found"
}
```

## 参考

- https://technet.microsoft.com/ja-jp/subscriptions/index/2009.01.windowspowershell
- https://www.mssqltips.com/sqlservertip/2714/introduction-into-handling-errors-in-powershell-for-sql-server-tasks/
