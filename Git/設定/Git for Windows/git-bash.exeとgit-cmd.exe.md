# git-bash.exeとgit-cmd.exe

- Git 2.xでは、Gitの実行バイナリとして、git-bash.exeとgit-cmd.exeがある。
- git-bash.exeはGUIアプリケーションで、エクスプローラーからアイコンをダブルクリックするとMinTTYが起動する。
  - なお、git-bash.exeはbash.exeのラッパーで、bash.exeを直接開いても同じ。
- git-cmd.exeはコンソールアプリケーションで、cmd.exeやConEmuのようなコンソールから起動する。
- ConEmuのデフォルトのgit-cmd.exe起動オプションは以下。

```bash
git-cmd.exe --no-cd --command=usr/bin/bash.exe -l -i
```
