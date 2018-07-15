﻿# レジストリを修正してCAPSLOCKの割り当て変更

## 方法

- レジストリエディタを開く。
- HKEY_CURRENT_USER\Keyboard Layout（またはHKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout）を開く。
  - 現在のユーザのみ設定したい場合は前者だが、環境によっては後者でなければ機能しない事もあるようだ？
- 右クリックして→「新規」→「バイナリ値」を作成して、名前を「Scancode Map」にする。
- Scancode Mapを開く。
- 以下のように値を設定する。

```powershell
0000 0000 0000 0000 
0200 0000 3800 3a00 
0000 0000
```

  - （解説）1列目のゼロ16個はヘッダなのでこの通りする。
  - 2列目最初の「0200 0000」は変更するキーの個数に末尾のターミネータを足した、設定値の個数。今回は1つのキーを設定するので、1+1で2となる。
  - 2列目残りの「3800 3a00 」は前半が変更後のスキャンコード、後半が変更対象のスキャンコード。リトルエンディアンなので、0038ではなく、3800のようにひっくり返す。

```powershell
変更後：「3800」 ALT左(0x38)
変更前：「3a00」 CapsLock(0x3A）
```

  - 3列目の末尾の「0000 0000」はターミネータ。必ずつける。
- レジストリエディタを終了して、PCを再起動する。

## スキャンコード一覧

|キー|キースキャンコード|レジストリで設定する値|
|-|-|-|
|Alt(右)|0xE038|38E0|
|Alt(左)|0x38|3800|
|CapsLock|0x3A|3A00|
|Ctrl(右)|0xE01D|1DE0|
|Ctrl(左)|0x1D|1D00|
|Esc|0x01||
|F11～F12|0x57～0x58||
|F1～F10|0x3B～0x44||
|NumLock|0x45||
|ScrollLock|0x46||
|Windows(右)|0xE05C|5CE0|
|Windows(左)|0xE05B|5BE0|
|ひらがな|0x70||
|スペース|0x39||
|半角/全角|0x29||
|変換|0x79||
|無変換|0x7B||

## 参考

- http://www.experts-exchange.com/OS/Microsoft_Operating_Systems/Windows/A_2155-Keyboard-Remapping-CAPSLOCK-to-Ctrl-and-Beyond.html
- http://msdn.microsoft.com/en-us/library/windows/hardware/gg463447.aspx
- http://www.jaist.ac.jp/~fujieda/scancode.html
- http://news.mynavi.jp/column/winxp/181/index.html
- http://blogs.msdn.com/b/shintak/archive/2013/02/21/10395636.aspx

```powershell
  Key            Scan                  
Num Label         Code   Symbolic Constant      Value
--- ------------- ----   ---------------------- --------  
  1  ~ `          29     VK_OEM_3               0xC0  
  2  ! 1          02                            0x31    
  3  @ 2          03                            0x32    
  4  # 3          04                            0x33    
  5  $ 4          05                            0x34    
  6  % 5          06                            0x35    
  7  ^ 6          07                            0x36    
  8  & 7          08                            0x37    
  9  * 8          09                            0x38    
 10  ( 9          0A                            0x39    
 11  ) 0          0B                            0x30    
 12  _ -          0C     VK_OEM_MINUS           0xBD
 13  + =          0D     VK_OEM_PLUS            0xBB
 15  Backspace    0E     VK_BACK                0x08
 16  Tab          0F     VK_TAB                 0x09
 17  Q            10                            0x51    
 18  W            11                            0x57
 19  E            12                            0x45    
 20  R            13                            0x52
 21  T            14                            0x54
 22  Y            15                            0x59
 23  U            16                            0x55
 24  I            17                            0x49
 25  O            18                            0x4F
 26  P            19                            0x50
 27  { [          1A     VK_OEM_4               0xDB  
 28  } ]          1B     VK_OEM_6               0xDD
 29  | \          2B     VK_OEM_5               0xDC
 30  Caps Lock    3A     VK_CAPITAL             0x14
 31  A            1E                            0x41
 32  S            1F                            0x53
 33  D            20                            0x44
 34  F            21                            0x46
 35  G            22                            0x47
 36  H            23                            0x48    
 37  J            24                            0x4A
 38  K            25                            0x4B
 39  L            26                            0x4C
 40  : ;          27     VK_OEM_1               0xBA
 41  " '          28     VK_OEM_7               0xDE
 42  (in'tl )     2B     
 43  Enter        1C     VK_RETURN              0x0D
 44  L SHIFT      2A     VK_SHIFT               0x10
 45  (in'tl )     56    
 46  Z            2C                            0x5A
 47  X            2D                            0x58
 48  C            2E                            0x43
 49  V            2F                            0x56
 50  B            30                            0x42    
 51  N            31                            0x4E
 52  M            32                            0x4D    
 53  < ,          33     VK_OEM_COMMA           0xBC 
 54  > .          34     VK_OEM_PERIOD          0xBE 
 55  ? /          35     VK_OEM_2               0xBF
 56  (in'tl )     73    
 57  R SHIFT      36    
 58  L CTRL       1D     VK_CONTROL             0x11
 60  L ALT        38     VK_MENU                0x12
 61  Space Bar    39     VK_SPACE               0x20
 62  R ALT        E0 38    
 64  R CTRL       E0 1D                                  
 75  Insert       E0 52  VK_INSERT              0x2D
 76  Delete       E0 53  VK_DELETE              0x2E
 79  L Arrow      E0 4B  VK_LEFT                0x25
 80  Home         E0 47  VK_HOME                0x24
 81  End          E0 4F  VK_END                 0x23
 83  Up Arrow     E0 48  VK_UP                  0x26
 84  Dn Arrow     E0 50  VK_DOWN                0x28
 85  Page Up      E0 49  VK_PRIOR               0x21
 86  Page Down    E0 51  VK_NEXT                0x22
 89  R Arrow      E0 4D  VK_RIGHT               0x27
 90  Num Lock     45     VK_NUMLOCK             0x90
 91  Numeric 7    47     VK_NUMPAD7             0x67 
 92  Numeric 4    4B     VK_NUMPAD4             0x64
 93  Numeric 1    4F     VK_NUMPAD1             0x61
 95  Num /        E0 35  VK_DIVIDE              0x6F
 95  LS+Num /     E0 B5 
 95  RS+Num /     E0 B6 
 96  Numeric 8    48     VK_NUMPAD8             0x68
 97  Numeric 5    4C     VK_NUMPAD5             0x65 
 98  Numeric 2    50     VK_NUMPAD2             0x62
 99  Numeric 0    52     VK_NUMPAD0             0x60
100  Numeric *    37     VK_MULTIPLY            0x6A
101  Numeric 9    49     VK_NUMPAD9             0x69 
102  Numeric 6    4D     VK_NUMPAD6             0x66
103  Numeric 3    51     VK_NUMPAD3             0x63
104  Numeric .    53     VK_DECIMAL             0x6E
105  Numeric -    4A     VK_SUBTRACT            0x6D
106  Numeric +    4E     VK_ADD                 0x6B
107  (in'tl )     7E  
108  NumEnter     E0 1C  VK_SEPARATOR           0x6C
110  Esc          01     VK_ESCAPE              0x1B
112  F1           3B     VK_F1                  0x70
113  F2           3C     VK_F2                  0x71
114  F3           3D     VK_F3                  0x72
115  F4           3E     VK_F4                  0x73
116  F5           3F     VK_F5                  0x74
117  F6           40     VK_F6                  0x75
118  F7           41     VK_F7                  0x76
119  F8           42     VK_F8                  0x77
120  F9           43     VK_F9                  0x78
121  F10          44     VK_F10                 0x79
122  F11          57     VK_F11                 0x7A
123  F12          58     VK_F12                 0x7B
124  PrintScreen  E0 A2  VK_SNAPSHOT            0x2C
124  Ctl+PrtScrn  E0 37
124  Shft+PrtScrn E0 37
124  Alt+PrtScrn  54
125  Scroll Lock  46     VK_SCROLL              0x91 
126  Pause        (??)   VK_PAUSE               0x13

L-Win             E0 5B  VK_LWIN                0x5B
R-Win             E0 5C  VK_RWIN                0x5C
Apps              E0 5D  VK_APPS                0x5D

------------ dedicated button scancodes ------------

                  E0 6A  VK_BROWSER_BACK        0xA6
                  E0 69  VK_BROWSER_FORWARD     0xA7
                  E0 67  VK_BROWSER_REFRESH     0xA8
                  E0 68  VK_BROWSER_STOP        0xA9
                  E0 65  VK_BROWSER_SEARCH      0xAA
                  E0 66  VK_BROWSER_FAVORITES   0xAB
                  E0 32  VK_BROWSER_HOME        0xAC

                  E0 20  VK_VOLUME_MUTE         0xAD
                  E0 2E  VK_VOLUME_DOWN         0xAE
                  E0 30  VK_VOLUME_UP           0xAF
                  E0 19  VK_MEDIA_NEXT_TRACK    0xB0
                  E0 10  VK_MEDIA_PREV_TRACK    0xB1
                  E0 24  VK_MEDIA_STOP          0xB2
                  E0 22  VK_MEDIA_PLAY_PAUSE    0xB3
                  E0 6C  VK_LAUNCH_MAIL         0xB4
                  E0 6D  VK_LAUNCH_MEDIA_SELECT 0xB5
compMgmtLauncher  E0 6B  VK_LAUNCH_APP1         0xB6
calc.exe          E0 21  VK_LAUNCH_APP2         0xB7
```
