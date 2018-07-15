# git reset（git add/commitの取り消し）

## 前提知識

ワーキングツリー
: 現在の状態

インデックス
: ワーキングツリーからgit addした状態

HEAD
: 最後にコミットした状態

HEAD^
: HEADの1つ前のコミットした状態

### git resetとは？
ワーキングツリーやインデックスやHEADの位置を移動する。（なお、コミットを修正する場合はgit commit --amendを使う。）

## git resetのオプションとその機能
### soft

```bash
git reset --soft HEAD^
```

HEADの位置をHEAD^へ変更する。インデックスとワーキングツリーに影響はない。

### mixed（またはオプションなし）

```bash
git reset --mixed HEAD
git reset HEAD
```

HEADの位置とインデックスをHEADへ変更する。ワーキングツリーに影響はない。

### hard

```bash
git reset --hard HEAD^
```

HEADの位置とインデックスとワーキングツリーをHEAD^へ変更する。

## 参考

- http://d.hatena.ne.jp/murank/20110327/1301224770
