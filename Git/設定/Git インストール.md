# Git インストール

## ソースコード
https://www.kernel.org/pub/software/scm/git/

## FreeBSD

```bash
./configure --prefix=/usr/local/git --enable-pthreads=-pthread --with-curl=/usr/local
gmake
gmake install
```
