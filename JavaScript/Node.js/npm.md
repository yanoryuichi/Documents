# npm


## パッケージ一覧

```clike
npm list -g
```

## パッケージインストール

```clike
npm install -g jshint
```

## パッケージアップデート
### パッケージ指定

```clike
npm update -g jshint
```

### 全パッケージ

```clike
npm update -g
```

## 設定
### 設定一覧

```clike
npm config ls -l
```

### 設定

```clike
npm conifg set HOME %APPDATA%
```

## 環境変数を使った設定

```clike
CMD> setx npm_config_userconfig "%APPDATA%\.npmrc"
Bash> export npm_config_userconfig $HOME/.npm/npmrc
```

- 環境変数をnpm_config_foo = barと指定する事で、任意のnpm configの設定が出来る。
- userconfigファイルの場所はuserconfigファイルには設定出来ないので、環境変数で設定する。

## Windowsでのnpmコマンドのアップグレード

- https://github.com/npm/npm/wiki/Troubleshooting#upgrading-on-windows
- http://qiita.com/hiroqn@github/items/93438c0c660025a53367

## 参考
https://npmjs.org/
