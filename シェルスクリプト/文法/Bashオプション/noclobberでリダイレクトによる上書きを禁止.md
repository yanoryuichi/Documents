# noclobberでリダイレクトによる上書きを禁止


## 設定を確認

```bash
$ set -o | grep noclobber
noclobber       off
```

## noclobberをオンにしてリダイレクトによる上書きを禁止する

```bash
$ set -o noclobber
$ touch 1.txt
$ date > 1.txt
-bash: 1.txt: cannot overwrite existing file
```

上書きしようとするとエラーが発生する。

## noclobberをオフにしてリダイレクトによる上書きを禁止を解除する

```bash
$ set +o noclobber
$ date > 1.txt
```

上書きOK。

## パイプを使ってnoclobbberによる上書き禁止を回避する

```bash
$ set -o noclobber
$ touch 1.txt
$ date > 1.txt
-bash: 1.txt: cannot overwrite existing file
$ date >| 1.txt
```

「>|」を指定する事で上書き禁止を回避出来る。
