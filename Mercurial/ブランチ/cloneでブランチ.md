# cloneでブランチ

## ユースケース
### 1. リポジトリをcloneしてブランチを作る

```clike
hg clone project01 project01-new
```

### 2. ブランチで作業する

```clike
cd project01-new
vi 1.txt
hg ci -m 'update 1.txt (branch)'
```

### 3. 元のリポジトリで作業する

```clike
cd ../project01
vi 1.txt
hg ci -m 'update 1.txt (original)'
```

### 4. ブランチの作業を元のリポジトリにmergeする

```clike
hg pull ../project01-new # pullして
hg glog                  # ログを見てリビジョン番号を確認する（今回はブランチでのコミットをリビジョン番号3とする）
hg id -n                 # ワーキングディレクトリのリビジョン番号も確認しておく
hg merge 3               # リビジョン番号を指定してmergeを実行する
```

### 5. merge結果をコミットする

```clike
hg ci -m 'merge #3'
```
