# BATプログラミング

## 条件分岐

```powershell
IF EXIST filename (
REM Do one thing
) ELSE (
REM Do another thing
)
```

## エコーバック制御

```powershell
@echo off
```

通常、BATファイルの先頭に記述して、コマンドのエコーバックをオフにする。

## コメント

```powershell
rem ################
rem  BAT Programing
rem ################
```

## 処理中断

```powershell
@echo off
date /t
pause
```

を実行すると、以下のようにpauseで処理を中断出来る。

```powershell
2013/07/14
続行するには何かキーを押してください . . .
```

## 引数

```powershell
notepad.exe %*
```

## リダイレクト・パイプ
### 標準出力

```powershell
dir foo > stdout.txt
```

### エラー出力

```powershell
mkdir foo 2> stderr.txt
```

### パイプ

```powershell
dir | nkf.exe -Sw > dir.txt
```

### エラー出力を標準出力に向ける

```powershell
mkdir foo 2>&1 | nkf -Sw > mesg.txt
mkdir foo 1> mesg.txt 2>&1
```

### /den/nullのようなもの

```powershell
mkdir foo 2> nul
```

## 組み込み変数
### バッチスクリプトのあるディレクトリの取得

```powershell
cd /d %~dp0
```

## 参考

- http://windows.g.hatena.ne.jp/cx20/20100203/p1
- http://www.confrage.com/dos/index.html
