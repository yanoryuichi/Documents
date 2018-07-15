# Select-StringとBashのgrepとの違い

### Select-StringとBashのgrepは役割が違う

- PowerShellのSelect-StringとBashのgrepは文字列を検索するという機能は似ているが、役割は違う。
- なぜかというと、Bashではコマンドの出力結果を|（パイプ）へ渡すが、パイプを介する入出力データは文字列（が前提とされる）。よって、コマンドの出力結果の抽出の為にgrepを多用する。
- 一方、PSではパイプから渡ってくるデータはオブジェクト。よって、通常は、コマンドレットの出力結果を文字列検索するのではなく、オブジェクト検索する。
- Select-Stringやgrepは文字列検索の為のコマンドである事、
- PSでSelect-Stringを使うのは、多くの場合、純粋にテキストファイルの中身を検索する際である事を理解しておく。

### Bashでのgrepでの典型的な使用例とPSでの同様な使用例

例えば、Bashでは以下のようなケースでgrepコマンドは頻繁に使われるが、

```powershell
Bash> ls -R * | grep ".txt"
Bash> ps -aux | grep "/usr/bin/python"
```

PSでは、

```powershell
PS> dir -r * | select-string ".txt"
PS> ps | select-string "chrome"
```

のようにSelect-Stringコマンドを普通は使わない。dirの出力結果としてパイプから渡るのはSystem.IO.FileInfoオブジェクトであり、psの出力結果はSystem.Diagnostics.Processオブジェクト。つまり、

```powershell
PS> dir -r -Path *.txt
PS> ps -Name *chrome*
```

のように、オブジェクトのプロパティを検索する。
