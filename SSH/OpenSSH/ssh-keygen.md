# ssh-keygen

## 作成

```
ssh-keygen -t rsa
```

### ファイル名を指定

```
ssh-keygen -t rsa -f ~/.ssh/foo
  => ~/.ssh/foo と ~/.ssh/foo.pubができる
```

### コメントを指定

```
ssh-keygen -t rsa -C this-is-my-key
```

## 鍵のフィンガープリントの確認

```
ssh-keygen -l -f ~/.ssh/id_rsa
```

```
-l Show fingerprint of specified public key file.  Private RSA1 keys are also supported.  For RSA and DSA keys ssh-keygen
   tries to find the matching public key file and prints its fingerprint.  If combined with -v, an ASCII art representa-
   tion of the key is supplied with the fingerprint.
```

### 暗号化 2010年問題

- RSA 1024ビットは避ける。2048ビットにする。
- ssh-keygen -t rsa で作成される鍵は2048ビット。
- https://www.ssl.ph/compare/useful/2010/

## 参考

http://serverfault.com/search?q=ssh+keygen+rsa
