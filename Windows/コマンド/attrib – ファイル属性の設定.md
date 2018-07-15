# attrib - ファイル属性の設定

## 属性
| 属性 | 内容 |
|-|-|
| R | 読み取り専用 |
| A | アーカイブ |
| S | システムファイル |
| H | 隠しファイル |
| I | インデックス対象外 |

## 属性の表示
### ファイルのみ表示

```powershell
attrib
```

### サブフォルダも含める

```powershell
attrib /s
```

### サブフォルダ・ディレクトリも含める

```powershell
attrib /s /d
```

### 個別にディレクトリを指定

```powershell
attrib dir1
```

## 属性の設定
### 隠しファイル属性の解除

```powershell
attrib -h C:\RECYCLE.BIN
```

### 隠しファイル・システムファイルの解除

```powershell
attrib -h -s desktop.ini
```

## 参考

- http://www.adminweb.jp/command/file/index8.html
- http://www.howtogeek.com/205910/how-to-change-file-attributes-with-attrib-from-the-windows-command-prompt/
