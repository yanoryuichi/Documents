# UTF-8 BOMの変換

## BOMの確認

### xxdコマンド
BOMなし

```bash
$ xxd utf8-no-bom.txt
00000000: 3132 330d 0a                             123..
```

"123"とだけ書かれたファイルとする。

BOMあり

```bash
$ xxd utf8-bom.txt
00000000: efbb bf31 3233 0d0a                      ...123.
```

先頭が"efbbbf"で、続いて"123"と書かれたファイル。

### fileコマンド
BOMなし

```bash
$ file utf8-no-bom.txt
utf8-no-bom.txt: ASCII text, with CRLF line terminators
```

BOMあり

```bash
$ file utf8-bom.txt
utf8-bom.txt: UTF-8 Unicode (with BOM) text, with CRLF line terminators
```

### BOM（バイトオーダーマーク）の実際
|エンコーディング | バイト列の実際 |h
| UTF-8 | 0xEF 0xBB 0xBF |
| UTF-16 BE | 0xFE 0xFF |
| UTF-16 LE | 0xFF 0xFE |

https://ja.wikipedia.org/wiki/%E3%83%90%E3%82%A4%E3%83%88%E3%82%AA%E3%83%BC%E3%83%80%E3%83%BC%E3%83%9E%E3%83%BC%E3%82%AF

## BOMの削除

### nkfコマンド

```bash
cat utf8-bom.txt | nkf --oc=utf-8
cat utf8-bom.txt | nkf -W -w80
```

http://www.atmarkit.co.jp/ait/articles/1609/29/news016.html

### sedコマンド

```bash
cat utf8-bom.txt | sed -e '1s/^\xef\xbb\xbf//'
```

### awkコマンド

```bash
cat utf8-bom.txt | awk '{if(NR==1)sub(/^\xef\xbb\xbf/,"");print}'
```

### tailコマンド

```bash
cat utf8-bom.txt | tail --bytes=+4
```

### 複数のファイルからまとめて削除

```bash
find . -type f -exec sed -i -e '1s/^\xEF\xBB\xBF//' {} \;
```

http://muzso.hu/2011/11/08/using-awk-sed-to-detect-remove-the-byte-order-mark-bom

## BOMの追加

### nkfコマンド

```bash
cat utf8-no-bom.txt | nkf --oc=utf-8-bom
```

### vim

```bash
vim utf8-no-bom.txt  # 1. vimで開く
:set bomb            # 2. :set bomb でBOMを設定する
:w utf8-bom.txt      # 3. :w で保存する
```
