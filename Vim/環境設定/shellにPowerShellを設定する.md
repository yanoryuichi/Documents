# shellにPowerShellを設定する

### .vimrc

```clike
if has('win32')
  set shell=C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
  set shellcmdflag=-c
  set shellquote=\"
  set shellxquote=
endif
```

### PSプロファイルを読み込まないプレーンなPowerShellを起動する場合

```clike
if has('win32')
  set shell=powershell.exe
  set shellcmdflag=-noprofile\ -nologo\ -c
  set shellquote=\"
  set shellxquote=
  set shellpipe=|
  set shellredir=>
  set shellcmdflag=/c\ powershell.exe\ -NoLogo\ -NoProfile\ -NonInteractive\ -ExecutionPolicy\ RemoteSigned
endif
```

## 参考
http://stackoverflow.com/questions/94382/vim-with-powershell
