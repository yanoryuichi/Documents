# デフォルト以外のリモートブランチにpushする

### デフォルトのリモートブランチにpushする

```bash
git push origin branch1 # (1)
git push                # (2)
```

- 普通はリモートにローカルと同名のbranch1ブランチが存在し、そこにpushする。 (1)
- origin branch1を省略することもできる。 (2)

### デフォルト以外の（別名の）リモートブランチにpushする

```bash
git push origin branch1:remote_branch2
```

- 「ローカルのブランチ名branch1：リモートのブランチ名remote_branch2」のように指定する。

### 補足

```bash
git push origin master        # (1)
git push origin master:master # (2)
```

- 普段(1)のようにmasterへプッシュするが、
- これは(2)のように指定するのと同じ。
