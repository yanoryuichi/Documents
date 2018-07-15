# ASCIIコード表の数値から文字に変換する

```bash
printf "%b\n" $(printf '%s%x' '\x' 97)
```

```bash
for n in $(seq 97 122); do
  printf "%b\n" $(printf '%s%x' '\x' $n)
done
```
ASCIIコード表の確認はman asciiで。
