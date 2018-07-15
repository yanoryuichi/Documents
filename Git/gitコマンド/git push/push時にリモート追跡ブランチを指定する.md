# push時にリモート追跡ブランチを指定する

```bash
git checkout master
git push -u origin master
```

- -u (--set-upstream) オプションを付けて、git pushする。
- 上の例ではローカルのmasterブランチはリモートのorigin/masterを追跡するようになる。

## 参考
https://git-scm.com/docs/git-push
