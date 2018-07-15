# タブ補完 autocompletion

### .bashrc

```bash
[[ -f /etc/bash_completion.d/git ]] && source /etc/bash_completion.d/git
```

- .bashrcなどに上のように記述する。

### autocompletionファイルが見つからない場合

```bash
 rpm -ql git | grep -i completion
```

- rpm系のOSでパッケージでGitをインストールしているなら、上のようにして探す。
- どうしても見つからない場合は、Gitの開発元から直接ダウンロードする。https://github.com/git/git の中のcontrib/completionにある。

## 参考
http://stackoverflow.com/questions/11173447/how-can-i-set-up-autocompletion-for-git-commands
