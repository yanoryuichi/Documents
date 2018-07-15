# Get-Member オブジェクトのメンバー一覧

あるオブジェクト（ここでは文字列"abc"）のメンバー（プロパティ・メソッド）一覧を取得する。

```powershell
PS C:\Users\taro> "abc" | Get-Member


   TypeName: System.String

Name             MemberType            Definition
----             ----------            ----------
Clone            Method                System.Object Clone()
CompareTo        Method                int CompareTo(System.Object value), int CompareTo(string strB)
Contains         Method                bool Contains(string value)
CopyTo           Method                System.Void CopyTo(int sourceIndex, char[] destination, int destinationIndex,...
（略）
```

## ファイルのメンバー一覧

```powershell
get-item 1.txt | get-member
```

## ファイル群のメンバー一覧

```powershell
dir | get-member
```

## 参考
http://technet.microsoft.com/ja-jp/library/dd315351
