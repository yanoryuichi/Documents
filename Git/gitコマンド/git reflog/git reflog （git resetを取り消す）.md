# git reflog （git resetを取り消す）


間違ってgit resetしてしまって元に戻したい場合、git reflogでHEADを調べて、git resetし直す。


## 作業例

今、↓のような状態にある。

```bash
git log
```

```bash
*       16ace8b na      2012-02-19 update 1.txt #3  (HEAD, master)
*       00da098 na      2012-02-19 update 1.txt #2
*       c99c449 na      2012-02-19 update 1.txt #1
*       66bb609 na      2012-02-19 add 1.txt
```

「update 1.txt #3」のコミットは間違いだったので、「update 1.txt #2」のコミットの状態に戻すために、git reset --hardする。

```bash
git reset --hard HEAD^^
```

が、HEAD^じゃなくてHEAD^^を指定してしまい、「update 1.txt #1」のコミットまで戻ってしまった。

```bash
git log
```

```bash
*       c99c449 na      2012-02-19 update 1.txt #1  (HEAD, master)
*       66bb609 na      2012-02-19 add 1.txt
```

こういう場合にgit reflogを実行する。

```bash
git reflog
```

```bash
c99c449 HEAD@{0}: HEAD^^: updating HEAD
16ace8b HEAD@{1}: commit: update 1.txt #3
00da098 HEAD@{2}: commit: update 1.txt #2
c99c449 HEAD@{3}: commit: update 1.txt #1
66bb609 HEAD@{4}: commit (initial): add 1.txt
```

とりあえずgit resetする前の状態（HEAD@{1}）に戻す為に、git resetをし直す。

```bash
git reset --hard HEAD@{1}
```

これで元に戻った。

```bash
git log
```

```bash
*       16ace8b na      2012-02-19 update 1.txt #3  (HEAD, master)
*       00da098 na      2012-02-19 update 1.txt #2
*       c99c449 na      2012-02-19 update 1.txt #1
*       66bb609 na      2012-02-19 add 1.txt
```

改めてgit resetする。

```bash
git reset --hard HEAD^
```

これで当初の目的通り、「update 1.txt #2」のコミットの状態になった。

```bash
git log
```

```bash
*       00da098 na      2012-02-19 update 1.txt #2  (HEAD, master)
*       c99c449 na      2012-02-19 update 1.txt #1
*       66bb609 na      2012-02-19 add 1.txt
```

### 参考
なお、ここまでやって、git reflogは以下のようになっている。

```bash
git reflog
```

```bash
00da098 HEAD@{0}: HEAD^: updating HEAD
16ace8b HEAD@{1}: HEAD@{1}: updating HEAD
c99c449 HEAD@{2}: HEAD^^: updating HEAD
16ace8b HEAD@{3}: commit: update 1.txt #3
00da098 HEAD@{4}: commit: update 1.txt #2
c99c449 HEAD@{5}: commit: update 1.txt #1
66bb609 HEAD@{6}: commit (initial): add 1.txt
```
