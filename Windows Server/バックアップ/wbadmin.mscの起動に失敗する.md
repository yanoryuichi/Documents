# wbadmin.mscの起動に失敗する

## 問題

- Windows Server バックアップのMSCを起動すると、「windows server ローカルバックアップで、状態の取得中にエラーが発生しました」というエラーメッセージが表示され、操作不能になる。

## 解決方法

- コマンドプロンプトを起動して、以下のコマンドを実行する。

```clike
wbadmin delete catalog
```

## 参考

- http://nasunoblog.blogspot.jp/2012/01/whs2011_14.html
