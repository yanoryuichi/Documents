# MacPortでFastCGIをインストール

```clike
sudo sysctl -w kern.sysv.shmall=32768
sudo sysctl -w kern.sysv.shmmax=134217728
```

/etc/sysctl.conf

```clike
kern.sysv.shmall=32768
kern.sysv.shmmax=134217728
```
