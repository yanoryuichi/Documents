# DisplayPort接続時にスリープ復帰後ウィンドウ位置消失を防ぐ

## 現象
DisplayPort接続時にスリープ復帰後ウィンドウ位置が消失して、ウィンドウが左上に寄ってしまう。

## 対応方法

- レジストリエディタを起動して、以下のキーを開く。
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GraphicsDrivers\Configuration\SIMULATED_XXX
- 00（及び00\00）内にPrimSurfSize.cxやPrimSurfSize.cy（ActiveSize.cxやActiveSize.cy）があり、その値は恐らく1024と768になっているので、使っているディスプレイの解像度の横や縦に変更する。
- 変更する場合は10進数を選んで数値を入力する。
- PCを再起動する。

## 注意
但し、上の方法を適用しても問題解決出来ない場合もある。また、マルチディスプレイ環境下では別のトラブルが発生する。一時的に解決してもディスプレイドライバやディスプレイ構成を変更すると、再度問題が発生する場合もある。その場合はHDMI等の別の接続方法を利用する。

## 参考
http://answers.microsoft.com/en-us/windows/forum/windows_7-hardware/windows-7-movesresizes-windows-on-monitor-power/1653aafb-848b-464a-8c69-1a68fbd106aa
