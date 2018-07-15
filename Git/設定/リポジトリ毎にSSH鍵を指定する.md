# リポジトリ毎にSSH鍵を指定する

## 前提

SSH 
: OpenSSH

リポジトリURL 
: git@bitbucket.org:foo/bar.git

秘密鍵 
: ~/.ssh/baz.key

## 手順

### 1. .ssh/configの設定

```bash
Host foo-bitbucket
   HostName bitbucket.org
   User git
   IdentityFile ~/.ssh/baz.key
   IdentitiesOnly yes
```

"Host"にユニークな名前（今回はfoo-bitbucket）を考えて指定する。SSHで接続する先のサーバ名（今回はbitbucket.org）はHostNameに書く。

### 2. git cloneの実行

```bash
git clone foo-bitbucket:foo/bar.git
```

正規のURL（サーバ名）であるbitbucket.orgは指定せずに、1.で考えたユニークな名前（foo-bitbucket）を指定して、git cloneする。
