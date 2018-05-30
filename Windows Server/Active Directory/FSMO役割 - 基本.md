# FSMO役割 - 基本

## FSMO役割を確認

```clike
C:\Users\administrator>netdom query fsmo /Domain:foodomain

スキーマ マスター                srv1.foodomain
ドメイン名前付けマスター         srv1.foodomain
PDC                              srv1.foodomain
RID プール マネージャー          srv1.foodomain
インフラストラクチャ マスター    srv1.foodomain
コマンドは正しく完了しました。
```

### 参考
http://www.atmarkit.co.jp/fwin2k/win2ktips/439fsmorole/fsmorole.html

## 参考
https://msdn.microsoft.com/ja-jp/library/cc773108(v=ws.10).aspx
