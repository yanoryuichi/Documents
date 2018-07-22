# CentOSでソースインストール

## 前提

- 環境・バージョン
  - CentOS 6.4
  - Mercurial 2.8
- インストール先
  - /usr/local/mercurial以下

## Mercurialのソースのダウンロード

```clike
mkdir /usr/local/src/mercurial
cd /usr/local/src/mercurial
wget wget http://mercurial.selenic.com/release/mercurial-2.8.2.tar.gz
```

- http://mercurial.selenic.com/downloads/

## Pythonのインストール

```clike
sudo yum install python-devel
sudo yum install python-docutils
```

## インストールディレクトリの作成

```clike
mkdir /usr/local/mercurial
```

## Mercurialのインストール

```clike
cd /usr/local/src/mercurial
tar zxvf mercurial-2.8.2.tar.gz
cd mercurial-2.8.2
make install PREFIX=/usr/local/mercurial
```

### 注意

- コンパイルする際にmake cleanした後にmake installすると
- "hg --version"の結果が"Mercurial Distributed SCM (version unknown)"になる。
- この場合、ソースコードを削除して、gzipから展開し直して、再度make installする。

### ドキュメントはインストールしない場合

```clike
make install-bin PREFIX=/usr/local/mercurial
```

## 参考

- http://mercurial.selenic.com/wiki/UnixInstall
- http://mercurial.selenic.com/
