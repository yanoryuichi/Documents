# VimShell

## インストールに必要なもの

- VimShellプラグイン
- VimProcプラグイン
  - vimproc.dll（コンパイル済みのもの）
- MinGW+MSYSのコマンド群（Windowsの場合）

## vimproc.dllの入手（コンパイル）

- Windowsの場合、以下にバイナリが配布されている。
  - https://github.com/Shougo/vimproc.vim/downloads
- また、KaoriyaのVimにはVimProcが同梱されていて、以下の場所にDLLが存在するので、それをコピーして使ってもいい。
  - $VIM\plugins\vimproc\autoload

### KaoriyaのVimのVimProc

- KaoriyaのVimにはVimProcが同梱されているが、最新のVimShellでは上手く動かない？ようなので、無効化して、最新のVimProcをインストールする。
- 無効化するには、$VIM\switches\catalogのdisable-vimproc.vimを$VIM\switches\enabledへコピーする。
- 但し、無効化しないでも、最新のVimProcを別のフォルダにインストールするだけで動いてるようにも見えるが、多分無効化した方が良いのでは？

## 参考
http://www.karakaram.com/windows-vimshell
