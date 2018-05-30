# クライアント Hyper-V


## インストール

- コントロールパネルを開き、[プログラムと機能]→[Windowの機能の有効化または無効化]を選ぶ。
- ダイアログが表示されるので、以下を選択して、OKを押す。
  - Hyper-V - Hyper-V プラットフォーム Hyper-Vをホストする為のサーバプログラム
  - Hyper-V - Hyper-V 管理ツール Hyper-Vホストに接続する、管理ツールプログラム

### 参考

- http://www.atmarkit.co.jp/ait/articles/1212/06/news103.html
- http://windows.microsoft.com/ja-jp/windows-8/hyper-v-run-virtual-machines

## PowerShellによるインストール


### Hyper-V関連機能の確認

```clike
PS> Get-WindowsOptionalFeature -Online -FeatureName "*hyper-v*" | ft -a

FeatureName                                State DisplayName                              Description
-----------                                ----- -----------                              -----------
Microsoft-Hyper-V-All                    Enabled Hyper-V                                  仮想マシンおよびそのリソー...
Microsoft-Hyper-V-Tools-All              Enabled Hyper-V 管理ツール                       Hyper-V を管理する GUI お...
Microsoft-Hyper-V-Management-Clients     Enabled Hyper-V GUI 管理ツール                   Hyper-V マネージャー スナ...
Microsoft-Hyper-V-Management-PowerShell  Enabled Windows PowerShell 用 Hyper-V モジュール Hyper-V を管理する Windows...
Microsoft-Hyper-V                       Disabled Hyper-V プラットフォーム                 仮想マシンとそのリソースの...
Microsoft-Hyper-V-Hypervisor            Disabled Hyper-V Hypervisor                       Hyper-V Hypervisor を提供...
Microsoft-Hyper-V-Services              Disabled Hyper-V サービス                         仮想マシンとそのリソースの...
```

### インストール

```clike
PS> Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

インストール後、再起動が必要。

### 参考

- https://technet.microsoft.com/en-us/library/hh846766.aspx
- http://social.technet.microsoft.com/wiki/contents/articles/15331.client-hyper-v-ja-jp.aspx
- https://technet.microsoft.com/en-us/library/hh852173.aspx
- https://www.petri.com/installing-hyper-v-on-windows-10
