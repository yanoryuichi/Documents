# svn resolve （ツリーコンフリクトの解消）

## ツリーコンフリクトが発生する状況
ローカル上のあるファイルをsvn delしたが、それをコミットする前に、誰かがそのファイルについて修正をコミットしていた場合等。

## ツリーコンフリクトの解消
上の状況の場合、svn revert xxx.txtでコンフリクトの状況を解消する。その上で以下のようにコマンドを実行する。

```bash
svn resolve --accept working filename
```

## 参考
http://svnbook.red-bean.com/en/1.7/svn.ref.svn.c.resolve.html
