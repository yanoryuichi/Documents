# 仮想インスタンス(Windows Server)のライセンス

## 物理インスタンスと仮想インスタンス

- 物理インスタンスとは、ホストOS（Windows Server）の事。
- 仮想インスタンスとは、ホストOS上にインストールするゲストOS（Windows Server）の事。

## 仮想インスタンスのライセンスの購入

- Windows Serverには標準で数個の仮想インスタンスライセンスが付属する。その個数を超えて、仮想インスタンスを動かしたい場合は、ライセンスを別途購入する必要がある。
- なお、仮想インスタンスのラインセンスはWindows Serverの事であり、LinuxやWindows 7/8等の他のOSは無制限にインストール出来る。（但し、例えばWindows 7なら、Windows 7のライセンスは必要。）

### Windows Serverに付属する仮想インスタンスライセンスの個数

```clike
Windows Server 2008 (R2) Standard   仮想インスタンスライセンス1
Windows Server 2008 (R2) Enterprise 仮想インスタンスライセンス4
Windows Server 2008 (R2) Datacenter 仮想インスタンスライセンス無制限
Windows Server 2012 (R2) Standard   仮想インスタンスライセンス2
Windows Server 2012 (R2) Datacenter 仮想インスタンスライセンス無制限
```

### 参考

- http://www.microsoft.com/ja-jp/server-cloud/windows-server/licenseguide/default.aspx の「OEM 版 Windows Server 仮想化ライセンスガイドダウンロード」にあるPDF資料
- http://www.vwnet.jp/Windows/WS08R2/License/Instance.htm
- http://www.microsoft.com/ja-jp/server-cloud/windows-server/licenseguide/Hyper-V-02.aspx

## Physical KeyとVirtual Key

- Physical Keyとは、物理マシンのWindowsプロダクトキー事。
- Virtual Keyとは、仮想マシンのWindowsプロダクトキーの事。

但し、Physical KeyとVirtual Keyの区別はWindows Server 2012から廃止され、物理インスタンスのプロダクトキーを仮想インスタンスでも使うようになった。

### 参考
http://www-06.ibm.com/jp/domino04/pc/support/Sylphd08.nsf/jtechinfo/SYJ0-0083FBE#501

## 参考

- http://www.microsoft.com/ja-jp/server-cloud/windows-server/licenseguide/Hyper-V-01.aspx
