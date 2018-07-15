# 別ユーザプロファイルにして特定サイト専用Chromeを作る

## 概要

- Chromeは起動時に--user-data-dirオプションを付けるとユーザプロファイルを格納するフォルダを指定できる。
- Chromeを起動するショートカットアイコンでこのオプションを付けて起動する事で、通常のユーザプロファイルとは別のユーザプロファイルでChromeを利用する事が出来る。
- また、起動オプションにURLを指定して、Chrome起動時に自動的に特定サイトが開かれるようにする。
- 今回はGmail専用Chromeを作る。このChromeはGmail専用な為、別のChromeを起動してGmailとは違うアカウントでGoogleにログインして、マルチアカウントでGoogleの各種サイトにアクセスする事が出来る。

## 手順
### ユーザプロファイルフォルダ作成

- 新しいユーザプロファイルを格納するフォルダを作る。今回は以下のようにした。
  - "C:\Users\taro\AppData\Roaming\Google2"

### Chromeのショートカットアイコンの作成

- Chromeの実行ファイルを探す。今回は以下の通りだった。
  - "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe"
- デスクトップ等に右ドラッグしてショートカットアイコンを作る。
- アイコンを右クリックしてプロパティを開く。
- リンク先が以下のようになっているので、
  - "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe"
- これを以下のように変更する。
  - "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" --user-data-dir="C:\Users\taro\AppData\Roaming\Google2" "https://mail.google.com/"
- ショートカットアイコンをダブルクリックしてChromeを起動する。
- タスクバー上のChromeのアイコンを右クリックして"タスクバーにピン留する"を選ぶ。
- これでこのアイコンでChromeを起動すると通常とは別のユーザプロファイルとなり、かつ指定したGmailのURLで起動する。

### ショートカットアイコンのアイコン画像変更

- http://www.easyicon.net/language.ja/ で適当なGmailのアイコンを探して、ダウンロードする。
- タスクバー上のChromeのアイコンを右クリックして「プロパティ」を開く。
- 「ショートカット」タブの「アイコンの変更」ボタンを押下する。
- 先ほどダウンロードしたアイコンファイルを指定する。
- OKでプロパティウィンドウを閉じる。

### プロファイルの確認

- ショートカットでChromeを起動する。
- アドレスバーに以下の文字列を入力して、表示されるプロフィールパスを確認する。

```
chrome://version/
```
