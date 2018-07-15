# RPMでインストール

## 前提

- OS: CentOS
- Suversionのリポジトリ: rpmforge

## rpmforgeの追加

```bash
rpm -ivh http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm
```

http://repoforge.org/use/

## 設定変更

```bash
vi /etc/yum.repos.d/rpmforge.repo
```

```bash
> enabled = 0
```

## Subversionのインストール

```bash
yum info subversion --disablerepo=\* --enablerepo=rpmforge-extras
yum install subversion --disablerepo=\* --enablerepo=rpmforge-extras
```
