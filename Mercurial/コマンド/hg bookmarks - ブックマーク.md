# hg bookmarks - ブックマーク


## 使用例
### 1. ワーキングディレクトリに入って、ブックマークを作成

```clike
cd HG_WORKING_DIR
```

```clike
hg bookmark my-tip
hg bookmark my-new-feature
```

### 2. 新機能ブックマークに入って、新機能をコミットする

```clike
hg update my-new-feature
```

```clike
vi 1.txt
hg ci -m "add a new feature on 1.txt"
```

### 3. TIPブックマークに入って、修正をコミットする

```clike
hg update my-tip
vi 1.txt
hg ci -m 'fix 1.txt'
```

### 4. TIPブックマークにて、新機能ブックマークをマージする

```clike
hg merge my-new-feature
```

## 参考

- http://mercurial.selenic.com/wiki/BookmarksExtension
- http://mercurial-users.jp/manual/hg.1.html#bookmarks
