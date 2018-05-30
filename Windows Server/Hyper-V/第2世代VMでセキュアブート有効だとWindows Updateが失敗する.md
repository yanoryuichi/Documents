# 第2世代VMでセキュアブート有効だとWindows Updateが失敗する

- 第2世代のVMを選択してWindows Server 2012をインストールすると、デフォルトでセキュアブートが有効になっている。
- この状態では初回のWindows Updateで必ず失敗する。
- これを回避するには、Hyper-V マネージャーから、VMの設定を編集し、セキュアブートのチェックを外す。
- 次にWindows Updateを行う。
- 初回のWindows Update後は、セキュアブートのチェックを戻しておいて良い。

### マイクロソフト セキュリティ アドバイザリ: 互換性のない UEFI ブート ローダー モジュールを無効にするための更新プログラム
> マイクロソフト セキュリティ アドバイザリ: 互換性のない UEFI ブート ローダー モジュールを無効にするための更新プログラム
> [URL] http://support.microsoft.com/kb/2871690/ja

## 参考

- http://oxfordsbsguy.com/2014/05/26/windows-update-fails-on-hyper-v-2012-r2-generation-2-virtual-machines/
- http://yamanxworld.blogspot.jp/2014/04/hyper-v-2-kb2871690.html
