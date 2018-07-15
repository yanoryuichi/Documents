# Alternate screen bufferを無効にする

## 目的
git log等でページャーでlessが起動するが、lessを終了すると画面がクリアされてしまう。これを防ぐには、Alternate screen bufferを無効にする。

## 手順

### 1. ターミナルを確認する

```bash
echo $TERM
cygwin
```

ターミナルはcygwin。

### 2. terminfoを作り変える

```bash
infocmp.exe > tmp.ti
vi.exe tmp.ti
```

（smcupとrmcupを削除）

```bash
tic.exe -o ~/.terminfo tmp.ti
```

- infocmpでテキストにダンプして、vi等で編集する。
- smcupとrmcupを削除して保存する。
- ticでterminfoを作り直す。
