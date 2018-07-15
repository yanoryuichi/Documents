# ShellNew(新規作成ファイル)を追加する

## 目的

- エクスプローラーの新規作成メニューで新規作成されるファイルを追加する。
- 今回は.phpファイルを追加してみる。
- OSはWindows 8とする。多分7以前でも同様と思う。

## 手順
### 拡張子とプログラムの関連付けを確認する

- コントロールパネルから「プログラム」→「既定のプログラム」→「関連付け」を開く。
- 拡張子.phpを探す。
- （以降は見つからなかった場合）
- デスクトップに、test.txtをリネームするかPowerShell等を利用して、test.phpを作る。
- test.phpを右クリックしてプロパティを開く。
- 「全般」タブの「プログラム：」の項の「変更...」ボタンを押下して、適切なエディタ等を選択する。今回はgvimにする。

### レジストリを編集する 1 - .php

- regeditを起動する。
- HKEY_CLASSES_ROOT\.php を開く。
- （既定）が恐らく「php_auto_file」になっているので、「phpfile」に変更する。phpfileでなくとも分かれば何でもよい。
- .php以下にShellNewというキーを作る（HKEY_CLASSES_ROOT\.php\ShellNewを作る。）
- ShellNew以下に文字列値を新規作成して、キーをNullFileに、値を空にする（編集ダイアログを表示して何も入力せずに閉じる）。
- 新規作成を追加するだけなら、この作業だけで良い。既定のアプリケーションを設定するには以下の作業も行う。

### レジストリを編集する 2 - php_auto_file

- HKEY_CLASSES_ROOT\php_auto_file を開く。
- php_auto_fileを右クリックして、エクスポートする。ここではphp_auto_file.regとして保存した。
- regeditを終了する。
- テキストエディタでphp_auto_file.regを開く。
- 以下のようになっているはずなので、

```powershell
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\php_auto_file]

[HKEY_CLASSES_ROOT\php_auto_file\shell]

[HKEY_CLASSES_ROOT\php_auto_file\shell\open]

[HKEY_CLASSES_ROOT\php_auto_file\shell\open\command]
@="\"C:\\Users\\taro\\App\\Vim\\gvim.exe\" \"%1\""
```

- 以下のように修正する。

```powershell
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\phpfile]
@="PHP File"

[HKEY_CLASSES_ROOT\phpfile\shell]

[HKEY_CLASSES_ROOT\phpfile\shell\open]

[HKEY_CLASSES_ROOT\phpfile\shell\open\command]
@="\"C:\\Users\\taro\\App\\Vim\\gvim.exe\" \"%1\""
```

- php_auto_file.regを保存して閉じる。
- php_auto_file.regをダブルクリックして、レジストリを更新する。

### 確認

- デスクトップを選択して、F5を数回押下する。
- デスクトップを右クリックして、「新規作成」の中に「PHP File」がある事を確認する。
- 見つからない場合はWindowsを再起動してみる。

```powershell
C:\Users\taro>assoc .php
.php=phpfile
```

```powershell
C:\Users\taro>ftype phpfile
phpfile="C:\Users\taro\App\Vim\gvim.exe" "%1"

```

## 参考

- http://help.lockergnome.com/windows/menu-work--ftopict583432.html
- http://homepage2.nifty.com/suyamsoft/Registry/Explorer/Association/index.html
