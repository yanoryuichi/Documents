# subversionをソースからインストール
$HOME以下にインストールする。うまく行かない時はパッケージで。
http://subversion.tigris.org/getting.html#binary-packages

## berkley dbをインストール

- http://www.oracle.com/technology/software/products/berkeley-db/db/index.html

```bash
cd build_unix/
../dist/configure --prefix=$HOME
make
make install
export LD_LIBRARY_PATH=$HOME/lib
export LD_RUN_PATH=$HOME/lib
```

## subversionをダウンロード

- http://subversion.tigris.org/
- http://subversion.tigris.org/servlets/ProjectDocumentList?folderID=0&expandFolder=0&folderID=260
- とりあえず圧縮ファイルを展開しておく。

## aprとapr-utilをダウンロード

- 以下のファイルをダウンロードして、それぞれapr/apr-utilという名前でsubversionのソースツリー直下に置く。
- http://apr.apache.org/
- http://ftp.kddilabs.jp/infosystems/apache/apr/apr-1.2.8.tar.gz
- http://ftp.kddilabs.jp/infosystems/apache/apr/apr-util-1.2.8.tar.gz

## subversionをインストール

```bash
./configure --prefix=$HOME --with-berkeley-db=$HOME
```
