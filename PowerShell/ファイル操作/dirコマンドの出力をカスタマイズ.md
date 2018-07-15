# dirコマンドの出力をカスタマイズ

## 目的

- dirコマンドの出力は標準では以下のようになる。
- ここではLengthの代わりにFileSizeという新しいファイルサイズを表すカラムにすることにする。
- FileSizeは新しいType Dataで、1000バイトなら1KBと表示するような型とする。（UNIXのls -hみたいなもの）

```powershell
    ディレクトリ: C:\tmp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       2017/02/12     19:22           4750 bar.txt
-a----       2017/02/12     19:22              0 foo.txt
-a----       2015/11/14     22:45          81711 baz.jpg
```

## 手順

### 1. Type Dataを作成する

```powershell

copy $PSHOME\Types.ps1xml $Env:USERPROFILE\Documents\WindowsPowershell\MyTypes.ps1xml
notepad $Env:USERPROFILE\Documents\WindowsPowershell\MyTypes.ps1xml
Update-TypeData -PrependPath $Env:USERPROFILE\Documents\WindowsPowershell\MyTypes.ps1xml
```

- システム標準のTypes.ps1xmlをマイドキュメント以下にコピーして、以下のように編集する。
- 編集が終わったら、ロードする。
- Get-ChildItem | Format-Table -Property Name, Length, FileSize を実行して、正しくロードできるか確認する。

```powershell
<?xml version="1.0" encoding="utf-8" ?>
<Types>
    <Type>
        <Name>System.IO.FileInfo</Name>
        <Members>
            <ScriptProperty>
                <!-- Filesize converts the length to a human readable
                    format (kb, mb, gb, tb) -->
                <Name>FileSize</Name>
                <GetScriptBlock>
                    switch($this.length) {
                        { $_ -gt 1tb } 
                            { "{0,4:n2} TB" -f ($_ / 1tb) ; break }
                        { $_ -gt 1gb } 
                            { "{0,4:n2} GB" -f ($_ / 1gb) ; break }
                        { $_ -gt 1mb } 
                            { "{0,4:n2} MB " -f ($_ / 1mb) ; break }
                        { $_ -gt 1kb } 
                            { "{0,4:n2} KB " -f ($_ / 1Kb) ; break }
                        default
                            { "{0,4} B " -f $_}
                    }
                </GetScriptBlock>
            </ScriptProperty>
        </Members>
    </Type>
</Types>
```

## 2. FileSystemのフォーマットファイルを修正

```powershell
copy $PSHOME\FileSystem.format.ps1xml $Env:USERPROFILE\Documents\WindowsPowershell\MyFileSystem.format.ps1xml
notepad $Env:USERPROFILE\Documents\WindowsPowershell\MyFileSystem.format.ps1xml
Update-FormatData -PrependPath $Env:USERPROFILE\Documents\WindowsPowershell\MyFileSystem.format.ps1xml
```

- システム標準のFileSystem.format.ps1xmlをマイドキュメント以下にコピーして、Lengthの箇所をFileSizeに修正する。
- 編集が終わったら、ロードする。

###
## 参考
http://superuser.com/questions/468782/show-human-readable-file-sizes-in-the-default-powershell-ls-command
