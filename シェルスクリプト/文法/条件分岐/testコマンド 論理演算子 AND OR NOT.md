# testコマンド 論理演算子 AND OR NOT

### AND

```bash
n1=10; n2=7
if [ "$n1" -gt 5 -a "$n2" -gt 5 ]; then echo OK; fi

```

### OR

```bash
n1=5; n2=10
if [ "$n1" -gt 7 -o "$n2" -gt 7 ]; then echo OK; fi
```

### 複雑な組み合わせ

```bash
n1=1; n2=10; n3=10
if [ \( "$n1" -gt 5 -a "$n2" -gt 5 \) -o "$n3" -gt 5 ]; then echo OK; fi
```

複雑な条件式の場合、複合コマンド[[]]を利用するのが無難。上のような通常のテストコマンドではn1が未定義などの場合、エラーが発生するので。

## NOT

```bash
if [ ! -f /tmp/1.txt -a ! -f /tmp/2.txt ]; then
  echo "no 1.txt, no 2.txt"
fi
```

## 参考

- http://www.ibm.com/developerworks/jp/linux/library/l-bash-test.html
- http://lagendra.s.kanazawa-u.ac.jp/ogurisu/manuals/sh-text/sh/node48.html
