# bashのカラーコード

|||||
|-|-|-|-|
|Black|0;30|Dark Gray|1;30|
|Blue|0;34|Light Blue|1;34|
|Green|0;32|Light Green|1;32|
|Cyan|0;36|Light Cyan|1;36|
|Red|0;31|Light Red|1;31|
|Purple|0;35|Light Purple|1;35|
|Brown|0;33|Yellow|1;33|
|Light Gray|0;37|White|1;37|

### 例：コマンドプロンプトを変更する

```bash
PS1="\[\033[01;33m\]test\033[0m\] "
```

"\[\033[01;33m\]"で色を設定して、"\[\033[0m\]" で色を元に戻す。

## 参考

- http://d.hatena.ne.jp/kakurasan/20080707/p1
