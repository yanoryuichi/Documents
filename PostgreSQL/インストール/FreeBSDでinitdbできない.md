# FreeBSDでinitdbできない

セマフォの初期値が小さいから。/boot/loader.confを以下のようにする。

```clike
kern.ipc.semmni=40
kern.ipc.semmns=240
kern.ipc.semume=40
kern.ipc.semmnu=120
```
