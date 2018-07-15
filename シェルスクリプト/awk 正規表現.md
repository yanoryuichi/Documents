# 正規表現でマッチする行

## 正規表現でマッチする行
### 全体

```bash
echo "hello world" | awk '/h/ { print }'
  hello world
```

### 1カラム目のみ

```bash
echo "hello world" | awk '$1 ~ /h/ { print }'
  hello world
```

## 正規表現でマッチしない行
### 全体

```bash
 echo "hello world" | awk '!/x/ { print }'
   hello world
```

### 1カラム目のみ

```bash
echo "hello world" | awk '$1 !~ /x/ { print }'
  hello world
```
