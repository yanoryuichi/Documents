# PSReadLine - コマンドライン編集機能強化

## PSReadLineとは？

- PowerShellにReadlineライクな行編集、キーバインドを実現するソフト。
- つまり、CTRL+Aでカーソルを行頭にしたり、CTRL+Lで画面をクリアしたり、CTRL+Pでコマンド履歴を検索したり出来る。
- PowerShellを使いこなすなら、必須と言っていいと思う。

## インストール

- https://github.com/lzybkr/PSReadLineからZIPファイルをダウンロードする。
- ZIPファイルを展開して出来たフォルダを  C:\Users\[User]\Documents\WindowsPowerShell\modules\PSReadline に置く。
- もしくは、PsGetでインストールするのが簡単。

## 設定
###  C:\Users\[User]\Documents\WindowsPowerShell\profile.ps1

```powershell
if ($host.Name -eq 'ConsoleHost')
{
   Import-Module PSReadline
}
```

### Emacsライクにする

```powershell
Set-PSReadlineOption -EditMode Emacs
```

### 追加設定
なぜかCTRL+PとCTRL+Nが標準でないので、追加する。

```powershell
Set-PSReadlineKeyHandler -Key 'Ctrl+p' -Function HistorySearchBackward
Set-PSReadlineKeyHandler -Key 'Ctrl+n' -Function HistorySearchForward
```

## 参考
http://blogs.technet.com/b/heyscriptingguy/archive/2014/06/19/useful-shortcuts-from-psreadline-powershell-module.aspx
