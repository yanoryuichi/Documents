# ライセンス認証管理 - slmgr

管理者権限に昇格したコマンドプロンプトより、slmgrコマンドを利用する。

### ライセンス情報の表示

```powershell
slmgr /dli
slmgr /dlv
```

- /dlvが詳細情報の表示。ライセンス期限やライセンス延長可能回数などが表示される。

### ライセンスの延長

```powershell
slmvr /rearm
```

- 元の有効期間だけ、ライセンス期限を延長できる。例えば90日間有効な評価版のOSなら、上のコマンドを実行することで90日延長できる。

### その他のオプション

```powershell
slmgr /?
```

## 参考

- http://www.atmarkit.co.jp/ait/articles/0809/19/news135.html
- http://www.atmarkit.co.jp/ait/articles/1005/28/news108.html
