# BS（バックスペース）キーが動かない

## はじめに

- OSはLinuxを前提とする。
- LinuxではBSキーは「CTRL+?」を送ることになっている。
- vimがBSキーから送られてくるコードをBSと認識していないので、BSキーが働かない。

## 対処方法
t_kbにBSキーで実際に送られるコードを設定し、fixdelする。以下のようなコードを.vimrcに書いておく。

```clike
if &term == "termname"
  set t_kb=^V<BS>
  fixdel
endif
```

^Vと<BS>の部分は、CTRLを押しながらVを入力し、続けてBSキーを押す事。

## 参考
bashやreadlineライブラリでのBS/DELETEキーの動作不良は、inputrcやbindなどで修正する。以下のURLなどを参考の事。

- http://www.ac.cyberhome.ne.jp/~yakahaira/vimdoc/options.html
- http://www.ac.cyberhome.ne.jp/~yakahaira/vimdoc/options.html
