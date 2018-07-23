# OSの判定

```clike
if has('unix') && system('which ack')
 set grepprg=ack\ -a
endif
```

## 参考
http://superuser.com/questions/194715/how-to-make-vim-settings-computer-dependent-in-vimrc
