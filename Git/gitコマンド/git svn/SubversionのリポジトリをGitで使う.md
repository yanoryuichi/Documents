# SubversionのリポジトリをGitで使う

1. svnレポジトリの作成とワーキングディレクトリのチェックアウト

```bash
 svnadmin create svn-repo
 svn co file:///$HOME/tmp/svn-repo svn-work
```

2. svnワーキングディレクトリにファイルを作成しコミット

```bash
 cd svn-work
 echo 1 > 1.txt
 svn add 1.txt 
 svn commit -m 'add 1.txt'
```

3. gitローカルリポジトリを作成

```bash
git svn clone file:///$HOME/tmp/svn-repo git-work
```

4. gitローカルリポジトリでファイルを編集し（gitの）コミット

```bash
cd git-work
echo 2 >> 1.txt 
git add 1.txt 
git commit -m 'edit 1.txt'
```

5. svnワーキングディレクトリ更新確認

```bash
cd $HOME/tmp/svn-work
svn up
```

この時点ではリビジョン1のまま

6. gitローカルリポジトリでsvn dcommitする

```bash
 cd $HOME/tmp/git-work
 git svn dcommit
```

7. svnワーキングディレクトリ更新確認

```bash
cd $HOME/tmp/svn-work
svn up
```

リビジョン2になっている

8. svnワーキングディレクトリでファイル編集しコミットする

```bash
cd $HOME/tmp/svn-work
echo 3 >> 1.txt 
svn commit -m 'edit'
```

9. gitローカルリポジトリを同期させて更新確認

```bash
git svn rebase
git log 1.txt
```
