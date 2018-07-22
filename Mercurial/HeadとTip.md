# HeadとTip

```clike

```

## リポジトリfooを作る

```clike
mkdir foo
cd foo
hg init
vi 1.txt
hg add 1.txt; hg commit -m 'add 1.txt'
```

## fooをクローンしてリポジトリbarを作る

```clike
cd ..
hg clone foo bar
```

## リポジトリfooでコミットをする

```clike
cd foo
vi 1.txt
hg commit -m 'update 1.txt'

```

## リポジトリbarでコミットをする

```clike
cd ../bar
hg heads
changeset:   0:5321ed0d2b1b
tag:         tip
user:        taro
date:        Thu Jul 12 20:14:30 2012 +0900
summary:     add 1.txt
```

```clike
vi 2.txt
hg add 2.txt; hg commit -m 'add 2.txt'
```

```clike
hg heads
changeset:   1:acaac151858a
tag:         tip
user:        taro
date:        Thu Jul 12 20:16:59 2012 +0900
summary:     add 2.txt
```

## リポジトリbarでpullする

```clike
hg pull
hg heads
changeset:   2:e48d7abcb233
tag:         tip
parent:      0:5321ed0d2b1b
user:        taro
date:        Thu Jul 12 20:15:14 2012 +0900
summary:     update 1.txt

changeset:   1:acaac151858a
user:        taro
date:        Thu Jul 12 20:16:59 2012 +0900
summary:     add 2.txt
```

```clike

```

## リポジトリbarでブランチを作る

```clike
hg branch br01
hg commit -m 'new branch br01'
vi 3.txt
```

```clike
hg add .\3.txt; hg commit -m 'add 3.txt'
hg update default
```

```clike
hg heads
changeset:   4:e1e322d25fbb
branch:      br01
tag:         tip
user:        taro
date:        Thu Jul 12 20:22:25 2012 +0900
summary:     add 3.txt

changeset:   2:e48d7abcb233
parent:      0:5321ed0d2b1b
user:        taro
date:        Thu Jul 12 20:15:14 2012 +0900
summary:     update 1.txt

changeset:   1:acaac151858a
user:        taro
date:        Thu Jul 12 20:16:59 2012 +0900
summary:     add 2.txt
```
