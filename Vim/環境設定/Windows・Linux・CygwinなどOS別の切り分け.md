# Windows・Linux・CygwinなどOS別の切り分け

```clike
if has("win64")
elseif has("win32")
elseif has("win32unix")
elseif has("osx")
elseif has("unix")
endif
```

## 参考

- http://vi.stackexchange.com/questions/2572/detect-os-in-vimscript
- http://auewe.hatenablog.com/entry/2013/05/14/003610
