# Beep音を止める

## コントロールパネルのサウンドを設定する

- コントロールパネルを開き、サウンドを開く。
- 「サウンド」タブを選び、「プログラムイベント」から「システム通知」を選ぶ。
- 「サウンド」を「Windows Background.wav」から「（なし）」にする。

## Beepサービスを停止する
### コマンド

```powershell
sc query beep                   # サービスの状態確認
sc stop beep                    # サービス停止
sc config beep start= disabled  # Windows起動時のサービス起動を無効化
```

## 参考

- http:/\/www.thewindowsclub.com/disable-system-beep-windows-7-8
- http://www.walkernews.net/2010/09/02/how-to-use-sc-command-to-disable-windows-7-beep-sound/
