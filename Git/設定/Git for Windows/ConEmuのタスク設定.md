# ConEmuのタスク設定

- GitはC:\App\Gitにインストールしたこととする。
- ウィンドウタイトル、タブのアイコン、起動ディレクトリを指定する。

### Git 2.x

```bash
-cur_console:t:"Git Bash":C:"C:\App\Git\mingw64\share\git\git-for-windows.ico":d:"C:\src" 
  C:\App\Git\git-cmd.exe --no-cd --command=usr/bin/bash.exe -l -i
```

### Git 1.x

```bash
-cur_console:t:"Git Bash":C:"C:\App\Git\etc\git.ico":d:"C:\src" 
  "C:\App\Git\bin\sh.exe" --login -i
```
