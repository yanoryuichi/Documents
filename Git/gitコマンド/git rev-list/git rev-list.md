# git rev-list

```bash
$ git rev-list master
e37250a Added bar.txt
3064cd4 Updated foo.txt
dcfff95 Added foo.txt
6ac92fa git init
```

```bash
$ git rev-list master
e37250a9a77e6cbxxc804c1a5824715e8efdb59f
3064cd4ba4fb92a83f0311041cb8b9c9c1a16c45
dcfff95814ca00f0c6230ba8c14eab0d86cdd9b8
6ac92fa41227a7a0b847972cbec35807459ce303
```

- git rev-listはGitの低レベルコマンド。
- git logに似ているが、他のコマンドにコミットIDを渡したい時などに使う。

## 参考

- https://git-scm.com/docs/git-rev-list/
