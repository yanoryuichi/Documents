# git log

## diffを表示する

```bash
git log --stat
```

他に

```bash
git log --numstat
git log --shortstat
```

## 他のブランチのログも表示する

```bash
git log --all
```

### 他のブランチのログも表示して、ツリー表示にする

```bash
git log --all --graph
```

```bash
* commit 09de85f42f988f2d5b1f7a50d278a2c8b39ec538
| Author: na <na>
| Date:   Sun Feb 19 12:46:25 2012 +0900
|
|     update 1.txt
|
| * commit d62c71a1764fd449ef8fac7dca1d5eb3da46b37c
|/  Author: na <na>
|   Date:   Sun Feb 19 12:45:27 2012 +0900
|
|       add 2.txt
|
* commit e514dac7778307714ffbabddf37b76d1a6717c04
  Author: na <na>
  Date:   Sun Feb 19 12:44:42 2012 +0900

      add 1.txt
```

↑は「add 2.txt」が別ブランチとして分岐している。

## ログフォーマットを指定して表示する

```bash
git log --color --format=full
git log --color --format=medium
git log --color --format=short
```

### ログフォーマットを個別指定して表示する

```bash
git log --graph --all --color --date=short --pretty='%x09%h %cn%x09%ad %s %Cred%d'
```

```bash
*       09de85f na      2012-02-19 update 1.txt  (HEAD, master)
| *     d62c71a na      2012-02-19 add 2.txt  (branch1)
|/
*       e514dac na      2012-02-19 add 1.txt
```

### それのエイリアスを設定する

```bash
git config --global alias.log2 "log --graph --all --color --date=short --pretty='%x09%h %cn%x09%ad %s %Cred%d'"
```

## 参考
http://transitive.info/article/git/command/log/
