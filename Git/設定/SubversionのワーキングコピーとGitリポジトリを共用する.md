# SubversionのワーキングコピーとGitリポジトリを共用する

### 1. プロジェクトディレクトリに入り、Subversionのファイルをチェックアウトする

```bash
cd project/
svn checkout file:///tmp/svn .
```

### 2. Subversionで.gitと.gitignoreを除外リストに指定する

```bash
svn propedit svn:ignore .
----------
.git
.gitignore
----------
svn commit -m 'Set svn:ignore' .
```

### 3. SubversionのワーキングコピーをGitで初期化する

```bash
cd project/
git init
```

### 4. Gitで.svnを除外リストに指定する

```bash
vi .gitignore
-----
.svn
-----
git add .gitignore
git commit .gitignore -m 'Set .gitignore'
```

### 5. GitでSubversion管理されているファイルをGitでも管理下に置く

```bash
git add .
git commit -m 'Added files from Subversion'
```
