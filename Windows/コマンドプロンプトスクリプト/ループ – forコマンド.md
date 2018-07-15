# ループ - forコマンド


## ループ

```powershell
CMD> for %v in (taro,jiro,hanako) do @echo %v

taro
jiro
hanako
```

### BATファイルにする場合、%%vのように%を重ねる

上のCMDをBATファイルに記述する場合、以下のようになる。

```powershell
@echo off
for %%v in (taro,jiro,hanako) do echo %%v
```


## /F ファイル読み取り

CMD.exe:

```powershell
CMD> for /f "" %v in (C:\tmp\users.txt) do @echo %v
```

BATファイル：

```powershell
@echo off
for /f "" %%v in (C:\tmp\users.txt) do @echo %%v
```


## 参考

- http://pf-j.sakura.ne.jp/program/dos/doscmd/for.htm
- http://ss64.com/nt/for.html
