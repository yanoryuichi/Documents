# git rebaseで複数のコミットを1つにまとめる

### 1. git logでコミットログを確認する

```bash
$ git log --oneline
71f4d70 commit#3
934d01c commit#2
7d19a73 commit#1
```

このうち、#2と#3を1つにまとめる事にする。

### 2. git rebaseを実行する

```bash
$ git rebase -i 7d19a73
```

#1のコミットIDである7d19a73を指定する。すると、以下のようにメッセージが出るので、

```bash
pick 934d01c commit#2
pick 71f4d70 commit#3
```

↓のように#3をs(squash)に指定する。

```bash
pick 934d01c commit#2
s 71f4d70 commit#3
```

### 3. コミットのやり直し

2.の続きでコミットメッセージの記述を促されるので、

```bash
# This is a combination of 2 commits.
# The first commit's message is:

commit#2

# This is the 2nd commit message:

commit#3
```

↓ 今回は以下のようにした。

```bash
commit#2 and commit#3
```

### 4. コミットログの確認

これで以下のように#2と#3のコミットがまとめられた。

```bash
$ git log --oneline
08984ad commit#2 and commit#3
7d19a73 commit#1
```
