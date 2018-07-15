# Universal Ctags

## インストール
### Windows

- https://ci.appveyor.com/project/masatake/ctags/branch/master を開く。
- JOB NAMEから、例えば64ビットWindowsなら、[Environment: compiler=msvc_msys2, ARCH=x64, MSYS2_ARCH=x86_64, MSYS2_DIR=msys64, MSYSTEM=MINGW64] を選ぶ。
- [ARTIFACTS]タブを選ぶ。
- "ctags-3093f73-x64.zip" のようなZIPファイルが見つかるので、ダウンロードする。
- ZIPファイルを展開して、中のctags.exeをパスの通った適当な場所にコピーする。

```
 - Win+Rキーでsysdm.cplを起動して、[詳細設定]→[環境変数]→[ユーザー環境変数]のPATHに追加するか、
 - CMDプロンプトから、setx "%PATH%;C:\tools\ctags" のようにする。
```

## 参考

- https://ctags.io/
- https://github.com/universal-ctags/ctags
