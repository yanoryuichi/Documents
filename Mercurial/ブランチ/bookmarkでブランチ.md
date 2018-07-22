# bookmarkでブランチ

## ユースケース
### 1. ブックマークを作って、修正開発用のブランチに入る

```clike
cd project01        # リポジトリに入る
hg id -n            # 現在のリビジョン番号を確認する（今回は2とする）
hg bookmark my-fix
```

### 2. 修正開発をして、コミットする

```clike
vi 1.txt
hg ci -m 'fix 1.txt'
```

### 3. 修正開発ブランチから元（のブランチ）に戻る

```clike
hg glog      # logを確認して、
hg update 2  # 元のリビジョンに更新する（上で確認したように今回は2）
```

### 4. 元のブランチで作業する

```clike
vi 1.txt
hg ci -m 'update 1.txt'
```

### 5. 修正開発のコミットを元のブランチにmergeする

```clike
hg merge my-fix
hg ci -m 'merge my-fix'
```
