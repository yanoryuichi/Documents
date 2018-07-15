# Windows Aero

## Aeroピークを制御する

- "コントロールパネル"→"システム"→”システムの詳細設定"を押下して、システムのプロパティを開く。
- "詳細設定"タブの"パフォーマンス"の"設定"ボタンを押下して、
- "視覚効果"タブの"プレビューを有効にする"チェックをオン（オフ）にする。

## Aeroシェイクを無効化する

- http://pasofaq.jp/windows/desktop/nowindowminimizingshortcuts.htm

## タスクバーサムネイルプレビュー

- How to Disable Taskbar Thumbnail Preview Windows 8.1/8/7 
- http://www.rushinformation.com/disable-taskbar-thumbnail-preview-windows-8-187/
  - HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer
  - TaskbarNoThumbnail Windows 8.1

## タスクボタンのライブサムネイルをポイントしてアクティブになるまでの時間

- レジストリエディタで以下のキーを開く。（なければ、作る。）
- HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\AdvancedのThumbnailLivePreviewHoverTime
- 値をミリ秒で指定する。（10進数なら、20000 -> 20秒。）

```powershell
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced]
"ThumbnailLivePreviewHoverTime"=dword:00004e20
```

### 参考

- http://news.mynavi.jp/column/windows/059/
- http://news.mynavi.jp/column/windows/060/
