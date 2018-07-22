# SSHの秘密鍵を指定する

##  手順

- TortoiseHg Workbenchを起動。
- ファイル→設定を開く。
- 「ファイルを開く」ボタンを押下。
- [ui]の項を以下のようにする。（ここでは折り返しているが実際には1行）

```clike
ssh = "C:\Program Files\TortoiseHg\TortoisePlink.exe" -ssh -2 -batch 
  -C -i "C:\Users\taro\ssh\id_rsa.ppk"
```

### パスフレーズ付きの秘密鍵を使う
PuTTYのpageant.exeを使って、予め秘密鍵をWindowsにロードして置く。

## 参考

Set up SSH for Mercurial 
: https://confluence.atlassian.com/display/BITBUCKET/Set+up+SSH+for+Mercurial

TortoiseHgでの複数 SSH IDの設定  
: http://confluence.atlassian.jp/pages/viewpage.action?pageId=35815540

Stack Overflow 
: http://stackoverflow.com/search?q=%5Btortoisehg%5D+ssh

PuTTY公式 plinkマニュアル 
: http://the.earth.li/~sgtatham/putty/0.63/htmldoc/Chapter7.html#plink
