# wslbridge

## wslbridgeとは？

- WSL(Bash on Windows)のターミナルソフトを標準のWindowsコンソール（コマンドプロンプト）でなく、MinTTYにする。
- MinTTYとはPuTTYから派生したCygwinの標準ターミナルソフト。
- Windowsコンソールは、表示のくずれ、フォントの選択など日本語対応に制限があり、BEEP音制御出来ないなど、欠点がある。
- Linux互換環境で使用するだけならMinTTYの方が優れるが、MinTTYはCygwin（MSYS）で使用するものであり、WSLでは使用できない。
- これを解決するのがwslbridge。
- wslbridgeを使うと、MinTTYを使ってWSLにアクセスできるようになる。

## ソースコード取得・コンパイル

- Cygwin（Msys2）とBash On Windowsでそれぞれフロントエンドとバックエンドをコンパイルする。

### Cygwin - frontend

```powershell
cd /tmp/
git clone https://github.com/rprichard/wslbridge.git
cd wslbridge/
cd frontend/
make
```

### WSL(Bash on Windows) - backend

```powershell
sudo apt-get install build-essential # ビルドツールがインストールされてなければインストールしておく

cd /tmp/
cd wslbridge/
cd backend/
make
```

## インストール

```powershell
cd /tmp/wslbridge/out/
cp  wslbridge.exe wslbridge-backend /c/cygwin/
```

- コンパイル後にoutディレクトリ以下に、wslbridge.exeとwslbridge-backendができる。
- この2つのファイルを適当なフォルダへコピーする。（CygwinやMsys2のフォルダー直下など）

## 起動

### Cygwin(MSYS2)から

```powershell
Cygwin Bash> mintty.exe -e "C:\cygwin\wslbridge.exe"
```


### MSYS2-launcherから

- MSYS2でMSYS2-launcherを導入していることとする。
- msys2.exeをコピーしてショートカットを作成する。
- ショートカットのプロパティを開き、リンク先を以下のようにする。
- C:\msys\msys2.exe "C:\msys\wslbridge.exe" -C~

## Cygwin(MSYS2）本体をインストールしたくない場合
### mintty.exe + cygwin1.dll(msys-2.0.dll)

- 以下のファイルを集めて、1か所にまとめる。
- mintty.exe
- cygwin1.dll (msys-2.0.dll)
- cygwin-console-helper.exe
- wslbridge.exe
- wslbridge-backend
- 参考 https://superuser.com/questions/1110045/windows-10-bash-and-mintty

```powershell

```

### WSLtty

- https://github.com/mintty/wsltty
- Cygwinプロジェクトがメンテナンスしてるので、オススメ。

## 参考

https://github.com/rprichard/wslbridge
