# git init

## リポジトリを作る

```bash
mkdir $HOME/tmp/project1; cd $HOME/tmp/project1
git init
```

## 共有リポジトリを作る

```bash
mkdir $HOME/tmp/project1.git; cd $HOME/tmp/project1.git
git init  --bare --shared=true
```

共有リポジトリは通常、拡張子.gitにする。

### --bareオプション

```bash
git init

drwxrwsr-x 3 taro taro 4096  2月 14 15:48 ./
drwxr-xr-x 7 taro taro 4096  2月 14 15:44 ../
drwxrwsr-x 7 taro taro 4096  2月 14 15:47 .git/
```

```bash
git init --bare

drwxrwsr-x 7 taro taro 4096  2月 14 15:50 ./
drwxr-xr-x 7 taro taro 4096  2月 14 15:44 ../
-rw-r--r-- 1 taro taro   23  2月 14 15:50 HEAD
drwxr-sr-x 2 taro taro 4096  2月 14 15:50 branches/
-rw-r--r-- 1 taro taro   66  2月 14 15:50 config
-rw-r--r-- 1 taro taro   73  2月 14 15:50 description
drwxr-sr-x 2 taro taro 4096  2月 14 15:50 hooks/
drwxr-sr-x 2 taro taro 4096  2月 14 15:50 info/
drwxr-sr-x 4 taro taro 4096  2月 14 15:50 objects/
drwxr-sr-x 4 taro taro 4096  2月 14 15:50 refs/
```
