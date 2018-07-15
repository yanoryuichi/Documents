# git revert （過去のコミットを取り消す逆パッチをコミットする）


### 概要

- 以下のように、あるファイルを編集して、3回コミットした。
- この3回のコミットのうち、2回目のコミット（f8584a4）を取り消す。
- コマンドは git revert f8584a4 。

```bash
1
2
3
```

↓

```bash
1 abc
2
3
```

↓

```bash
1 abc
2
3 xyz
```

このログは以下。

```bash
* 7043fc5 (HEAD -> master) #3
* f8584a4 #2
* b1e6157 #1
```

### 手順

```bash
$ git revert f8584a4
[master 1ee7c5a] Revert "#2"
1 file changed, 1 insertion(+), 1 deletion(-)
```

git revertした結果、ファイルは以下のようになった。

```bash
1
2
3 xyz
```

ログは以下。

```bash
* 1ee7c5a (HEAD -> master) Revert "#2"
* 7043fc5 #3
* f8584a4 #2
* b1e6157 #1
```
