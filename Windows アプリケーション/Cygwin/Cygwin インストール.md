# Cygwin インストール

## Chocolateyでインストール

```
choco install cygwin
```

- 上のコマンドで、C:\tools\cygwin以下に全てインストールされる。

### 参考
https://chocolatey.org/packages/Cygwin

## インストールオプション
### Installation Directory

```
C:\cygwin
```

- ルートディレクトリ。C:\cygwin\bin,C:\cygwin\home,C:\cygwin\etc等が出来る。

### Local Package Directory

```
C:\cygwin\packages
```

- ローカルパッケージ（bashやgrep等の圧縮ファイル）が保存される。

```
 - "C:\cygwin\packages\http%3a%2f%2fftp.jaist.ac.jp%2fpub%2fcygwin%2f\x86_64\release\bash\bash-4.3.39-2.tar.xz"
 - "C:\cygwin\packages\http%3a%2f%2fftp.jaist.ac.jp%2fpub%2fcygwin%2f\x86_64\release\grep\grep-2.21-2.tar.xz"等
```

## Chocolateyでインストール先を指定してインストール

```
choco install cygwin -o -ia "-q -N -R C:\cygwin -l c:\cygwin\packages"
```

- 上のコマンドでsetup.exeが起動し、オプションが指定された状態でインストール作業が促される。
- このコマンドの場合、C:\cygwinがRoot install directoryになり、C:\cygwin\bin,C:\cygwin\home,C:\cygwin\etc等が出来る。
- また、c:\cywgin\packagesにはLocal package（bashやgcc等の圧縮ファイル）が保存される。
- setup.exeはC:\tools\cygwin以下に設置される。

### 参考
http://qiita.com/ko2ic/items/2574139dd095e5a31e76

## setup.exeのコマンドラインオプション

```
Command Line Options:
-D --download                     Download from internet
-L --local-install                Install from local directory
-s --site                         Download site
-O --only-site                    Ignore all sites except for -s
-R --root                         Root installation directory
-x --remove-packages              Specify packages to uninstall
-c --remove-categories            Specify categories to uninstall
-P --packages                     Specify packages to install
-C --categories                   Specify entire categories to install
-p --proxy                        HTTP/FTP proxy (host:port)
-a --arch                         architecture to install (x86_64 or x86)
-q --quiet-mode                   Unattended setup mode
-M --package-manager              Semi-attended chooser-only mode
-B --no-admin                     Do not check for and enforce running as
                                  Administrator
-h --help                         print help
-l --local-package-dir            Local package directory
-r --no-replaceonreboot           Disable replacing in-use files on next
                                  reboot.
-X --no-verify                    Don't verify setup.ini signatures
-n --no-shortcuts                 Disable creation of desktop and start menu
                                  shortcuts
-N --no-startmenu                 Disable creation of start menu shortcut
-d --no-desktop                   Disable creation of desktop shortcut
-K --pubkey                       URL of extra public key file (gpg format)
-S --sexpr-pubkey                 Extra public key in s-expr format
-u --untrusted-keys               Use untrusted keys from last-extrakeys
-U --keep-untrusted-keys          Use untrusted keys and retain all
-g --upgrade-also                 also upgrade installed packages
-o --delete-orphans               remove orphaned packages
-A --disable-buggy-antivirus      Disable known or suspected buggy anti virus
                                  software packages during execution.
```

http://superuser.com/questions/214831/how-to-update-cygwin-from-cygwins-command-line

## 参考
http://cygwin.com/cygwin-ug-net/cygwin-ug-net.html
