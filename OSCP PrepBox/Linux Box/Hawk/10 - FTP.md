## FTP anonymous login
```bash
$ ftp 10.10.10.102
Connected to 10.10.10.102.
220 (vsFTPd 3.0.3)
Name (10.10.10.102:dix): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    2 ftp      ftp          4096 Jun 16  2018 messages
226 Directory send OK.
ftp> cd messages
250 Directory successfully changed.
ftp> dir -a
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    2 ftp      ftp          4096 Jun 16  2018 .
drwxr-xr-x    3 ftp      ftp          4096 Jun 16  2018 ..
-rw-r--r--    1 ftp      ftp           240 Jun 16  2018 .drupal.txt.enc
226 Directory send OK.
ftp> get .drupal.txt.enc
local: .drupal.txt.enc remote: .drupal.txt.enc
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for .drupal.txt.enc (240 bytes).
226 Transfer complete.
240 bytes received in 0.00 secs (1.2576 MB/s)

```

```bash
cat .drupal.txt.enc 
U2FsdGVkX19rWSAG1JNpLTawAmzz/ckaN1oZFZewtIM+e84km3Csja3GADUg2jJb
CmSdwTtr/IIShvTbUd0yQxfe9OuoMxxfNIUN/YPHx+vVw/6eOD+Cc1ftaiNUEiQz
QUf9FyxmCb2fuFoOXGphAMo+Pkc2ChXgLsj4RfgX+P7DkFa8w1ZA9Yj7kR+tyZfy
t4M0qvmWvMhAj3fuuKCCeFoXpYBOacGvUHRGywb4YCk=
```

```bash
$ base64 -d .drupal.txt.enc > drupal-encrypt
```

```bash
$ cat drupal-encrypt 
Salted__kY ԓi-6l7Z>{$p5 2[
8?sWj#T$3AG,f   Z\ja>>G6
.EÐVV@ɗ4@w
```

```bash
$ file drupal-encrypt 
drupal-encrypt: openssl enc'd data with salted password
```

divisible by 8, most likely a block cipher
```bash
wc -c drupal-encrypt 
176 drupal-encrypt
```

### decrypting
```bash
$ bruteforce-salted-openssl -t 10 -f /usr/share/wordlists/rockyou.txt -c aes-256-cbc -d sha256 drupal-encrypt 
Warning: using dictionary mode, ignoring options -b, -e, -l, -m and -s.

Tried passwords: 22
Tried passwords per second: inf
Last tried password: 123123

Password candidate: friends


^C
┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/hawk/ftp]
└──╼ [??]$ openssl enc -aes-256-cbc -d -in drupal-encrypt -out drupal-decrypted -k friends
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/hawk/ftp]
└──╼ [??]$ cat drupal-decrypted 
Daniel,

Following the password for the portal:

PencilKeyboardScanner123

Please let us know when the portal is ready.

Kind Regards,

IT department

```