# ファイルにvimの設定を埋め込む

> モードラインの書き方の具体例
> 
> 各モードラインの書き方の具体的な例を挙げると、下記のようになります。
> 
> 「書き方 その1」は「se[t]」を書かかなくても良いのですが、 
> その行、モードライン以降にvimエディタのオプション以外の余分な文を書くことができません。 
>  「書き方 その2」はモードライン以降に余分な文やコメントを書くことができますが、 
>  「se[t]」と、モードラインを閉じる「:」を書く必要があります。
> モードラインの書き方 その1
> vim: expandtab fenc=cp932 ff=unix ft=rest
> 
> モードラインの書き方 その2
> vim: set expandtab fenc=cp932 ff=unix ft=txt :
> 
> モードラインの書き方 その2（余分なテキストつき）
> vim: set expandtab fenc=cp932 ff=unix ft=txt : # この行はvimエディタのモードラインです。

## 参考
http://nanasi.jp/articles/howto/file/modeline.html
