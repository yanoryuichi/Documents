# 引数解析 - echoargs.exe(PSCX)

echoargs.exeはPowerShellがどのように引数を解析しているか調べるコマンド。PowerShell Community Extensions(PSCX)に含まれている。

## 使用例
例えばmvnコマンドが上手く動かない場合、mvnコマンドをechoargsで解析すると、

```powershell
PS C:\Users\taro\Documents\tmp> echoargs mvn archetype:create -DgroupId=jp.co.example -DartifactId=mvntest
Arg 0 is <mvn>
Arg 1 is <archetype:create>
Arg 2 is <-DgroupId=jp>
Arg 3 is <.co.example>
Arg 4 is <-DartifactId=mvntest>
```

上のようにjp.co.exampleが途切れている事が分かる。従って、mvnコマンドを動かす場合は、以下のように"-DgroupId=jp.co.example"と引用符でくるんであげればよい。

```powershell
PS C:\Users\taro\Documents\tmp> mvn archetype:create "-DgroupId=jp.co.example" -DartifactId=mvntest
```
