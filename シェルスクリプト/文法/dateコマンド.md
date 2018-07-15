# dateコマンド

## 前日

```bash
date -d '1 days ago' +"%Y%m%d"
```

## 10日後

```bash
date -d '10 days' +%Y%m%d
```

## 指定された日付の翌日

```bash
date -d '2014-04-01 1 days' +%Y%m%d
```

## 月末

```bash
date -d "$(date -d "next month" +%Y-%m-1) -1 day" +%Y-%m-%d  # 今月末
date -d "$(date -d "2 month" +%Y-%m-1) -1 day" +%Y-%m-%d     # 来月末
date -d "$(date +%Y-%m-1) -1 day" +%Y-%m-%d                  # 先月末
date -d "$(date -d "-1 month" +%Y-%m-1) -1 day" +%Y-%m-%d    # 2か月前の月末
```

## 指定した日より連続N日

```bash
seq 1 3 | xargs -i date +%Y%m%d -d "{} day ago"
 
20170517
20170516
20170515
```

この場合、本日2017年5月18日とすると、前日17日からの3日間前。

### シェル変数に格納

```bash
dt=`date -d "$(date -d "next month" +%Y-%m-1) -1 day" +%Y-%m-%d`
echo $dt
```

## YYYY-MM-DD HH:II:SSな形式

```bash
date +"%Y-%m-%d %H:%M:%S"
  => 2014-12-03 12:51:36
```
