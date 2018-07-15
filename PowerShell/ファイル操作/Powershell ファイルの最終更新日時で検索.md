# Powershell ファイルの最終更新日時で検索

```powershell
PS> dir .\tmp\ | ft -a

Mode         LastWriteTime Length Name
----         ------------- ------ ----
-a--- 2015/08/17     19:08      5 1.txt
-a--- 2015/08/17     18:09      0 2.txt

PS> [datetime]$theday = "2015-08-17 18:50:00"

PS> dir -R tmp | ? { $_.LastWriteTime -gt $theday } | ft -a

Mode         LastWriteTime Length Name
----         ------------- ------ ----
-a--- 2015/08/17     19:08      5 1.txt
```
