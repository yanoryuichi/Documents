# VimBallでインストール先を指定する

## 目的
ここではlocalvimrc.vbaというプラグインを$HOME/.vim/bundle/localvimrcディレクトリ以下にインストールする。

## 方法
### 1. インストール先のディレクトリを事前に作る

```clike
mkdir $HOME/.vim/bundle/localvimrc
```

### 2. プラグインのインストール

```clike
vi localvimrc.vba
```

```clike
:UseVimball $HOME/.vim/bundle/localvimrc
```

## 参考
### インストールするファイルの確認

```clike
vi localvimrc.vba
```

```clike
:VimballList
```
