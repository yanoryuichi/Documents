# testコマンド 戻り値判定

## 通常の判定

```bash
[ "a" = "a" ] && echo "OK"
```

```bash
if [ "a" != "b" ]; then
  echo "OK"
fi
```

## 特殊変数$?による判定

```bash
[ "a" = "a" ]
if [ $? -eq 0 ]; then
   echo "OK"
fi
```

## 参考

- http://www.ibm.com/developerworks/jp/linux/library/l-bash-test.html
- http://lagendra.s.kanazawa-u.ac.jp/ogurisu/manuals/sh-text/sh/node48.html
