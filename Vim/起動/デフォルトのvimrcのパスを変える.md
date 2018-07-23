# デフォルトのvimrcのパスを変える

## コマンドラインオプション -u でvimrc指定して起動する

```clike
vi -u /tmp/vim/vimrc foo.txt
```

### -u NONE でvimrcやプラグインを読み込まないで起動する

```clike
vi -u NONE
```

## 環境変数 VIMINIT で読み込む対象のディレクトリを指定する

```clike
export VIMINIT=/tmp/vim
vi foo.txt
```

## 参考
http://stackoverflow.com/questions/7109667/change-default-location-of-vimrc
