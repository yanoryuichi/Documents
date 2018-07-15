# diffoolにWinMergeを使う

## .gitconfig

```bash
 [diff]
	tool = winmerge
 [difftool "winmerge"]
	cmd = "'C:/Program Files (x86)/WinMerge/WinMergeU.exe'" -e -u -dl "Base" -dr "$REMOTE" "$LOCAL" "$REMOTE"
 [difftool]
	prompt = false
```

## WinMergeコマンドラインオプション
http://manual.winmerge.org/Command_line.html
