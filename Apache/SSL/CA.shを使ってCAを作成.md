# CA.shを使ってCAを作成

ここではLinuxのUbuntuをOSとする。

## CA作成スクリプトの用意

```clike
mkdir /etc/ssl/CA
cd /etc/ssl/CA
cp /usr/lib/ssl/misc/CA.sh ,
vi CA.sh
```

CA.shを編集して、CADAYS="-days 3650"とした。

## CAの作成

```clike
DAYS=3650 CATOP=myCA ./CA.sh -newca
```

```clike
CA certificate filename (or enter to create)

Making CA certificate ...
Generating a 1024 bit RSA private key
.....++++++
...++++++
writing new private key to './demoCA/private/./cakey.pem'
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:JP
State or Province Name (full name) [Some-State]:N/A
Locality Name (eg, city) []:N/A
Organization Name (eg, company) [Internet Widgits Pty Ltd]:N/A
Organizational Unit Name (eg, section) []:N/A
Common Name (eg, YOUR name) []:myCA0531.local
Email Address []:
```

### CA証明書作成時の質問について
CAとCSRを発行するホストが同一の場合、Country NameやOrganization Name等が同じで無ければならないらしいので、必要な箇所だけ入力し、後は適当な文字で埋めると良い。

## openssl.cnfの修正

```clike
cp /usr/lib/ssl/openssl.cnf .
vi openssl.cnf
```

dir = ./myCAとする。以後、opensslコマンドを使う場合はこのcnfファイルを読み込むように指定すると良い。
