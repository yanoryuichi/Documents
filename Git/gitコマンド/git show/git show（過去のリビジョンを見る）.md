# git show（過去のリビジョンを見る）

```bash
git show HEAD test.txt
git show 71de6e3f77d1f059feaedab763850faf29723a00:test.txt
```

もしくは

```bash
git cat-file -p HEAD:test.txt
```
