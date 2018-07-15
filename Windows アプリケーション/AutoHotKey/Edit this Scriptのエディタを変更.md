# Edit this Scriptのエディタを変更

- レジストリ HKEY_CLASSES_ROOT\AutoHotkeyScript\Shell\Edit\Command の値を変更する。
  - 例："C:\Users\taro\App\Vim\gvim.exe" "%1"
  - 既定：notepad.exe %1

```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\AutoHotkeyScript\Shell\Edit\Command]
@="\"C:\\Users\\taro\\App\\Vim\\gvim.exe\" \"%1\""
```

## 参考
http://www.autohotkey.com/board/topic/23889-how-to-edit-this-script-in-any-editor-other-than/
