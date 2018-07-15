# リポジトリ新規作成（tunk,branches,tagsも一緒に）

```bash
svnadmin create $HOME/svn-repos
mkdir -p $HOME/work/tmp/{trunk,branches,tags}
svn import $HOME/work/tmp file:///$HOME/svn-repos -m 'make dirs'
```
