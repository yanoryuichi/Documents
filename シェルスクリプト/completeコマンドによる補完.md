# completeコマンドによる補完

以下はsshコマンドを入力する際に.ssh/known_hostsからホスト名を抜き出して補完する。.bashrc等に設定する。

```bash
function ssh_complete() {
 local curw
 COMPREPLY=()
 curw=${COMP_WORDS[COMP_CWORD]}
 ORIG=$IFS
 IFS="
  "
 COMPREPLY=($(compgen -W '$(cut -f 1 -d " " $HOME/.ssh/known_hosts)' -- $curw))
 IFS=$ORIG
 return 0
}
complete -F ssh_complete ssh
```

- completeコマンドによってコマンドを補完する。最後の引数sshが補完される対象のコマンド。
- completeコマンドは様々な引数を取れるが、-Fによってシェル関数を呼び出すことが出来る。
- シェル関数内で、COMPREPLY配列変数にキーワードを設定し、補完候補にする。
- 補完候補を作る場合、compgenコマンドを利用すると、絞り込み検索が出来る。
  - 補完候補がfoo1 foo2 barとあった場合、fまで入力してTABを押すと、foo1とfoo2のみ候補になる。
- COMP_WORDSは入力中のコマンドライン文字列をホワイトスペースでsplitした配列変数。

### 上の修正版

```bash
function ssh_complete() {
 local curw
 local hosts=()
 COMPREPLY=()
 curw=${COMP_WORDS[COMP_CWORD]}
 ORIG=$IFS
 IFS="
 "
 if [ -f "$HOME/.ssh/known_hosts" ]; then
   hosts=(${hosts[@]} $(cut -f 1 -d " " $HOME/.ssh/known_hosts))
 fi
 if [ -f "$HOME/.ssh/config" ]; then
   hosts=(${hosts[@]} $(grep '^Host ' "$HOME/.ssh/config" | cut -f 2 -d ' '))
 fi
 COMPREPLY=($(compgen -W '${hosts[@]}' -- $curw))
 IFS=$ORIG
 return 0
}
```
