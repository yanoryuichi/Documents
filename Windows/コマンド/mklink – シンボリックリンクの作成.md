# mklink - シンボリックリンクの作成

```powershell
mklink notepad.exe "C:\Windows\notepad.exe"
```

リンク先のファイル名の拡張子は、リンク元のファイル名の拡張子と同じくする。拡張子を省略したリンクは作成しない。

## 管理者権限なしでシンボリックリンクを作る

- Windows 10でCreatro's Update以降は管理者モードを有効にすることで管理者権限なしでシンボリックリンクを作れるようになった。
- 設定アプリを起動して、更新とセキュリティ→開発者向けを開くと、「開発者モード」を選べる。詳しくは以下を参考のこと。
- https://www.howtogeek.com/292914/what-is-developer-mode-in-windows-10/
- なお、現在のところ、PowerShellでNew-Item -Type Symboliclinkを行うには管理者権限が必要。現在、開発対応中のようだ？
