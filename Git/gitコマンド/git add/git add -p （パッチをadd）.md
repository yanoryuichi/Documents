# git add -p （パッチをadd）


### ステージングする
1. git add -pで対話的にaddする。

```bash
$ git add -p 1.txt
diff --git a/1.txt b/1.txt
index 01e79c3..280c8b8 100644
--- a/1.txt
+++ b/1.txt
@@ -1,3 +1,5 @@
 1
+a
 2
 3
+b
Stage this hunk [y,n,q,a,d,/,s,e,?]? 
```

2. sを選び、hunkをsplitする。

```bash
Stage this hunk [y,n,q,a,d,/,s,e,?]? s
Split into 2 hunks.
@@ -1,3 +1,4 @@
 1
+a
 2
 3
Stage this hunk [y,n,q,a,d,/,j,J,g,e,?]?
```

3. yを選び、このhunkをaddする。

```bash
Split into 2 hunks.
@@ -1,3 +1,4 @@
 1
+a
 2
 3
Stage this hunk [y,n,q,a,d,/,j,J,g,e,?]?y
```

4. nを選び、このhunkをaddしない。

```bash
@@ -2,2 +3,3 @@
 2
 3
+b
Stage this hunk [y,n,q,a,d,/,K,g,e,?]?n
```

これでステージングが終わった。


### ステージング状態の確認
git statusで確認。

```bash
$ git st
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   1.txt
#
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#       modified:   1.txt
#
```

git diff --cachedでも確認。

```bash
$ git diff --cached 1.txt
diff --git a/1.txt b/1.txt
index 01e79c3..1920040 100644
--- a/1.txt
+++ b/1.txt
@@ -1,3 +1,4 @@
 1
+a
 2
 3
```

### commitする

```bash
$ git commit -m 'modify #1' 1.txt
```


### 改めてgit diff

```bash
$ git diff
diff --git a/1.txt b/1.txt
index 1920040..280c8b8 100644
--- a/1.txt
+++ b/1.txt
@@ -2,3 +2,4 @@
 a
 2
 3
+b 
```

### 2回目のaddとcommit

```bash
$ git add 1.txt
$ git commit 1.txt -m 'modify #2'
```
