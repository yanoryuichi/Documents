# sttyコマンド

## echoを抑制

```bash
#!/bin/bash

echo -n "Input your passwd: "
stty -echo
read input_data
stty echo
echo
echo Your passwd: $input_data
```

## 参考
http://linuxjm.sourceforge.jp/html/GNU_sh-utils/man1/stty.1.html
