# ディスク増設 - diskpart

## diskpartコマンドの起動

```clike
C:\> diskpart
```

## ディスク一覧表示

```clike
DISKPART> list disk
```

空き（Free）が0Bなディスクが新しく増設したディスク。


## ディスクの選択

```clike
DISKPART> select disk 1
```

list diskコマンドの表示結果の先頭カラムのディスク番号を使ってディスクを選択する。ここでは1を選択した。

## パーティション一覧表示

```clike
DISKPART> list partition
```

ディスクを選択した後にlist partitionコマンドを実行する。

## ボリューム一覧表示

```clike
DISKPART> list volume
```

Ltrはドライブレター。Cドライブとか。

## パーティションの作成

```clike
DISKPART> create partition primary size=60000
```

ディスクを選択した後にcreate partitionコマンドを実行する。ここではサイズを60GBで指定したが、指定しないとそのディスクすべてを指定した事になる。

## ボリュームのファイルシステムの確認

```clike
DISKPART> select vololume 1
DISKPART> filesystems
```

## ボリュームのフォーマット

```clike
DISKPART> format fs=ntfs label="Data Vol 1" quick
```

## ドライブレターの割り当て

```clike
DISKPART> select vololume 1
DISKPART> assign letter=g 
```

## パーティション・ボリュームの削除

```clike
DISKPART> select vololume 1
DISKPART> delete volume
```

```clike
DISKPART> select partition 1
DISKPART> delete partition
```

## diskpartコマンドの終了

```clike
DISKPART> exit
```

## 参考
http://www.atmarkit.co.jp/fwin2k/win2ktips/1115dpartcmd/dpartcmd.html
