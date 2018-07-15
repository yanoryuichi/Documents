# ctags

## コマンド

```clike
ctags -R --languages=PHP --langmap=PHP:.php.inc \
  --php-types=c+f+d /home/taro/src/my_app/ /usr/local/php/lib/php/symfony/
```

## ソースコード

- http://prdownloads.sourceforge.net/ctags/ctags-5.8.tar.gz

## インストール

```clike
./configure --prefix=$HOME/opt/ctags
make
make install
```

## 日本語版

- http://hp.vector.co.jp/authors/VA025040/ctags/

## 参考

- Exuberant Ctags http://ctags.sourceforge.net/
- http://www.asahi-net.or.jp/~wv7y-kmr/memo/vim_php.html
