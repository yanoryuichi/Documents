# エンコーディングがUTF8以外のテキストファイルを扱う

- GitはテキストファイルのエンコーディングがUTF8であることを前提に動作する。
- UTF16などの他のエンコーディングのファイルはバイナリ扱いになり、git diffやgit showが期待するようには動作しない。
- これに対処するために、UTF16向けのフィルターを作り、git diff実行時はこのフィルターを使うようにする。

## 参考

- http://genjiapp.com/blog/2014/07/26/git-diff-utf-16-text-files.html
- https://andrewnaylor.co.uk/git-localizable-strings/

### BOMについて
https://www.medo64.com/2015/05/bom-away-in-git-style/
