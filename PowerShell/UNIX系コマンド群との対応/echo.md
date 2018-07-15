# echo

## Write-OutputとWrite-Host

- Write-Outputはコマンドレットの結果をパイプラインに渡す。Wite-Hostはコマンドレットの結果をパイプラインに渡さない。
- コマンドレットの終端でechoしたい時はWrite-Hostを使う。

```powershell
PS> function Receive-Output
{
    process { Write-Host $_ -ForegroundColor Green }
}

PS> Write-Output  "this is a test" | Receive-Output   # "thie is a test" は緑で表示される
PS> Write-Host "this is a test" | Receive-Output      # "thie is a test" は白（デフォルト色）で表示される
PS> Write-Output  "this is a test"                    # "thie is a test" は白（デフォルト色）で表示される
```

### 参考
http://windowsitpro.com/powershell/q-should-i-ever-use-write-host-powershell
