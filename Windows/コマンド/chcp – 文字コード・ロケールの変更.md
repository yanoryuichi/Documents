# chcp - 文字コード・ロケールの変更

## 文字コード・ロケールの確認

```powershell
chcp
```

日本語Windowsの既定では「932」。
## 文字コード・ロケールの設定

```powershell
chcp 65001
```

### 英語にする

```powershell
chcp 437
```

## コードページ一覧

|||
|-|-|
| 932 | shift_jis |
| 20127 | us-ascii |
| 65001 | utf-8 |

### 参考

- http://msdn.microsoft.com/en-us/library/dd317756(VS.85).aspx

## コマンドプロンプトのフォントをMSゴシックにする

- 以下のようにレジストリに"0."というキーを作り、値をMSゴシックにする。

```powershell
reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Console\TrueTypeFont" /v 0. /t REG_SZ /d "MS Gothic"
```

- マシンを再起動する。
- コマンドプロンプトを開き、chcp 65001を実行後、プロパティ（既定値）を開き、フォントタブのフォントの一覧にMSゴシックを表示されるはずなので、それを選ぶ。
- 上で上手く動かない場合は、コマンドプロンプトを起動しなおし、コードページがSJIS（chcp 932）の状態である事を確認してから、プロパティ（既定値）でフォントをMSゴシックに指定する。その後、chcp 65001を実行し、再度フォントを指定する。

### 参考

- http://takuya-1st.hatenablog.jp/entry/20110115/1295078608
- http://www26.atwiki.jp/ghostwind/pages/88.html
- http://stackoverflow.com/questions/3222213/how-can-i-change-console-font/3222490#3222490
- http://www.hanselman.com/blog/UsingConsolasAsTheWindowsConsoleFont.aspx
- http://extstrg.asabiya.net/pukiwiki/index.php?%A5%B3%A5%DE%A5%F3%A5%C9%A5%D7%A5%ED%A5%F3%A5%D7%A5%C8%A4%CE%CA%B8%BB%FA%A5%B3%A1%BC%A5%C9%CA%D1%B9%B9
