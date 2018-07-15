# Explorerのコンテキストメニューから項目を削除する

## Git Cheetahでインストールした場合
以下のようにGitのインストールフォルダにCMDで入り、regsvr32を実行する。Windowsが32bitか64bitで実行する内容を変える事。

```bash
cd C:\Program Files (x86)\Git\git-cheetah
regsvr32 /u git_shell_ext64.dll
regsvr32 /u git_shell_ext.dll
```

## レジストリでインストールした場合

- レジストリエディタで修正するか、ShellExViewを使う。
- もしくは、Git for Windowsをインストールし直す。

## 参考
http://stackoverflow.com/questions/2459763/how-do-i-remove-msysgits-right-click-menu-options
