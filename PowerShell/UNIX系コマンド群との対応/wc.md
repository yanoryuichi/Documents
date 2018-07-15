# wc

## ファイル/ディレクトリの数をカウントする

```powershell
ls -1 | wc -l  # Bash
dir | measure  # PowerShell
```

## ファイルサイズの合計を求める

```powershell
dir | measure -property length -sum
```
