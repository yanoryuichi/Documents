# cpでファイルバックアップ時に元ファイルの上書きを防ぐ

```bash
#!/bin/sh
cp -uv file.txt file.txt.orig
＜略＞
touch file.txt.orig
```

cpコマンドの-uオプションを使いコピーファイルを作り、元ファイルをtouchしておく。-uオプションは更新があった場合にのみファイルコピーするので、上のスクリプトを2回以上実行してもオリジナルのfile.txtはfile.txt.origとして残り続ける。
