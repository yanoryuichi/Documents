# depthオプション

## depthオプションとは

- depthオプションで、svn checkout等のターゲットのディレクトリ下をどのように参照するか指定する。
- set-depthオプションで、そのディレクトリのdepthのフラグを設定できる。
- depthオプションの引数（フラグ）は以下。
  - files
  - empty
  - immediates
  - infinity

## 前提

```bash
PROJECT_ROOT
|-- Makefile
|-- bin
|   `-- foo.exe
|-- doc
|   `-- README.txt
`-- lib
    |-- bar.dll
    `-- baz
        `-- baz.dll

4 directories, 5 files
```

## --depth empty ファイルもディレクトリも参照しない

```bash
$ svn co file:///$HOME/tmp/repos/ --depth empty working-copy
$ cd working-copy
$ ls
（何もない）
$ svn up
$ ls
（何もない）
$ svn up Makefile
$ ls
Makefile
```


## --depth files ファイルだけ参照する
別のワーキングコピーでdoc/install/install.txtが追加され、doc/README.txtが更新され、コミットされた。

```bash
$ cd OHTER_WORKING_COPY/
$ svn commit -m 'update'
追加しています              doc/install
追加しています              doc/install/install.txt
送信しています              doc/README.txt
```

このワーキングコピーでdocディレクトリ以下のファイルだけ取り出すように--set-depth filesでフラグを付けて、svn updateする。

```bash
$ cd THIS_WORKING_COPY
$ svn up --set-depth files doc
U    doc/README.txt
```

README.txtファイルだけ更新された。以後、このワーキングコピーではdocディレクトリ以下はファイルだけしか参照しない。

```bash
$ svn up doc
$ ls doc/
README.txt
```

## --depth immediates 直下のファイルとディレクトリだけ参照する

```bash
$ svn co file:///$HOME/tmp/repos/ --depth immediates somefiles
A    somefiles/doc
A    somefiles/lib
A    somefiles/bin
A    somefiles/Makefile
```

## --depth infinity ファイルも更新も再帰的に参照する

```bash
$ svn co file:///$HOME/tmp/repos/ --depth infinity allfiles
A    allfiles/doc
A    allfiles/doc/install
A    allfiles/doc/install/install.txt
A    allfiles/doc/README.txt
A    allfiles/lib
A    allfiles/lib/bar.dll
A    allfiles/bin
A    allfiles/bin/foo.exe
A    allfiles/Makefile
```

## 参考
http://svnbook.red-bean.com/en/1.6/svn.advanced.sparsedirs.html
