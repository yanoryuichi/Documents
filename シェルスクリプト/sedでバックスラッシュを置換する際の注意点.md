# sedでバックスラッシュを置換する際の注意点

## シェル展開の挙動について
正規表現を'（シングルクォート）でくくる場合、置換文字列「＼＼」がシェル展開されずにsedに伝わる。sedは「＼＼」を「＼」と解釈し、結果を表示する。

```bash
> echo "[／]" | sed -e 's／＼／／＼＼／'
[＼]
```

正規表現を"（ダブルクォート）でくくる場合、置換文字列「＼＼＼＼」はシェル展開されて「＼＼」に変わる。sedは「＼＼」を「＼」と解釈し、結果を表示する。~
なお、「＼＼＼」をシェル展開しても「＼＼」になる。「＼＼＼＼＼」をシェル展開すると「＼＼＼」に変わる。この挙動はしっくりこないが、基本的に「＼＼＼＼」を「＼＼」に展開する方針を採った方が分かりやすいだろう。

```bash
> echo "[／]" | sed -e "s／＼／／＼＼＼＼／"
 [＼]
```

## 正規表現にシェル変数を使うには？
正規表現に与える文字列では「＼」をエスケープしなければならない。「/etc/passwd」に対して「/etc」を「/tmp」に置換するようなケースを考えてみる。~
Perlで言えば以下のようにすることで、「/tmp/passwd 」と表示される

```bash
$etc_passwd = "/etc/passwd";
$etc_passwd  =~ s#/etc#/tmp#;
print $etc_passwd;

```

まず「／etc」を「＼／etc」とする。

```bash
etc="／etc"
escaped_etc=`echo $etc | sed -e 's／＼／／＼＼＼＼＼／／g'`
echo $escaped_etc
```

「＼＼＼＼＼／」は前半4文字と後半2文字で分けて考える。

まず前半4文字「＼＼＼＼＼」を考える。最初にバッククォートによるシェル展開で「＼＼＼＼」が「＼＼」に展開される。次にsedによる解釈で「＼＼」が「＼」に変わる。~
次に後半2文字「＼／」を考える。最初にバッククォートによるシェル展開で「＼／」が「／」に展開される。次に「／」はsedに文字通り解釈される。

```bash
etc_passwd="／etc／passwd"
tmp_passwd=`echo "$etc_passwd" | sed -e "s／^$escaped_etc／＼／tmp／"`
echo $tmp_passwd
```

続き、実際にetcをtmpに置換するsedを考える。~
$escaped_etcにはエスケープされた「＼／etc」が入っている。バッククォートによるシェル展開で「／etc」になり、sedはそれを文字通り解釈する。~
また、「＼／tmp／」もバッククォートによるシェル展開で「／tmp」になり、sedはそれを文字通り解釈する。

以上で、「／etc／passwd」が「／tmp／passwd」に置換された。全部をシェルスクリプトにすると以下の通り。

```bash
#!/bin/sh

etc="/etc"
escaped_etc=`echo $etc | sed -e 's/\//\\\\\//g'`
etc_passwd="/etc/passwd"
tmp_passwd=`echo "$etc_passwd" | sed -e "s/^$escaped_etc/\/tmp/"`
echo $tmp_passwd
```

## 本当は、

```bash
$ echo '1/2/3' | sed -e s'#/#,#g'
1,2,3
```

これでいいんだけど。
