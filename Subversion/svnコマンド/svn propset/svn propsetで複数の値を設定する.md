# svn propsetで複数の値を設定する

- 以下のように複数の値をsvn propsetしようとしても、値は追加登録されず、上書きされる。後者の*.gifのみ有効となる。

```bash
svn propset svn:ignore '*.jpg' .
svn propset svn:ignore '*.gif' .
```

- 複数の値を設定するには、
- 1. svn propeditしてエディタが起動するので、そこで記述するか、

```bash
svn propedit svn:ignore .
-----
*.jpg
*.gif
-----
```

- 2. テキストファイルに値を記述して保存し、そのファイルをsvn propset -Fオプションで指定して読み込ませるか、

```bash
vi ignores.txt
-----
*.jpg
*.gif
-----
svn propset svn:ignore -F ignores.txt .
```

- いずれかの方法を取る。

## 参考
http://stackoverflow.com/questions/86049/how-do-i-ignore-files-in-subversion
