# Windows向けSSHクライアント

- Windows向けSSHクライアントは、開発が継続しているプロジェクトが多数ある。
- もっとも有名なのはPuTTY。恐らくシェアは断然1位と思われる。
- PuTTYは公式版の開発も継続されているが、KiTTYやSuperPuttyのような派生版が多くある。国内の派生版ではiceiv+puttyが高機能で有名。
- PuTTYはSSHクライアントと指定外に、WinSCPやTortoiseSVNなどSSH関連ソフトで内部的に使われており、CygwinやMSYS2に付属するMinTTYもPuTTYをベースにしている。
- PuTTY以外では、個人的な印象ではSecureCRTがよく使われている。さらにこれら以外では、X Server機能などSSH以外の機能を備えたMobaXterm、RDP機能で有名なmRemoteNGも比較的有名と思われる。
- 国内のSSHクライアントとしてはTeraTermが一番有名だと思われるが、すでに国内でもPuTTYが優勢で、昔ほどには利用されてないと思われる。Poderosaも同様に今ではあまり使われてない印象。
- それ以外の国内のSSHクライアントでは、RLoginが大変高機能で開発が活発に進んでおり、今後とても期待できる。
- また、Windows 10からはWSL(Bash On Widows)が搭載され、Windowsコンソール（コマンドプロンプト）をSSHクライアントとして使うことも可能だが、Windowsコンソールはターミナルソフトとしての機能が貧弱で、日本語環境では特に問題がある。WIN32-OpenSSHのようなWindows版OpenSSHも含めて、SSHの機能面より、ターミナルソフトの機能面で実用に問題がある。
- WSLではWSLttyを使うのが良いと思われる。WSLttyは、MinTTYでWSL環境へ、SSH経由ではなく直接bash.exeに対して、アクセスできるようにするターミナルソフト。
- WSLは安定しており、CygwinやMSYS2よりも高速。Windowsの標準機能であり、今後の開発継続が期待できる。したがって、SSHクライアントとしてだけ使うなら、CygwinやMSYS2の存在価値はあまりなく、WSLに切り替えた方が良いと思われる。

### PUTTY

- 公式版 https://www.chiark.greenend.org.uk/~sgtatham/putty/
- KiTTY http://www.9bis.net/kitty/
- iceiv+putty http://ice.hotmint.com/putty/

### SecureCRT

- https://www.vandyke.com/products/securecrt/

### MobaXterm

- http://mobaxterm.mobatek.net/

### mRemoteNG

- https://mremoteng.org/

### RLogin

- http://nanno.dip.jp/softlib/man/rlogin/
