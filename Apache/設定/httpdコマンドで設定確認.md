# httpdコマンドで設定確認

## syntaxチェック

```clike
httpd -t
```

## バーチャルホスト一覧表示

```clike
httpd -S
```

## 静的モジュール一覧表示

```clike
https -l
```

## 静的+DSOモジュール一覧表示

```clike
httpd -M
```

## バージョン情報・コンパイル情報表示

```clike
httpd -V
```

## 参考
http://httpd.apache.org/docs/2.4/programs/httpd.html
