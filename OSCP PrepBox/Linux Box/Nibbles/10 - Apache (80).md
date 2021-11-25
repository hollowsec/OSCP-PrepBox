# Web Server on 80

* Nibbleblog
Version: v4.0.3
Codename: Coffee
Release date: 2014-04-01

## Fuzzing files/api
```bash
$ ffuf -u http://10.10.10.75/nibbleblog/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-small-words.txt                                                                             
                                                                                                                                                                                              
        /'___\  /'___\           /'___\                                                                                                                                                       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.75/nibbleblog/FUZZ
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-small-words.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

.htm                    [Status: 403, Size: 301, Words: 22, Lines: 12]
.php                    [Status: 403, Size: 301, Words: 22, Lines: 12]
admin                   [Status: 301, Size: 321, Words: 20, Lines: 10]
.html                   [Status: 403, Size: 302, Words: 22, Lines: 12]
plugins                 [Status: 301, Size: 323, Words: 20, Lines: 10]
themes                  [Status: 301, Size: 322, Words: 20, Lines: 10]
content                 [Status: 301, Size: 323, Words: 20, Lines: 10]
languages               [Status: 301, Size: 325, Words: 20, Lines: 10]
.                       [Status: 200, Size: 2987, Words: 116, Lines: 61]
.htaccess               [Status: 403, Size: 306, Words: 22, Lines: 12]
.php3                   [Status: 403, Size: 302, Words: 22, Lines: 12]
.phtml                  [Status: 403, Size: 303, Words: 22, Lines: 12]
README                  [Status: 200, Size: 4628, Words: 589, Lines: 64]
.htc                    [Status: 403, Size: 301, Words: 22, Lines: 12]
.php5                   [Status: 403, Size: 302, Words: 22, Lines: 12]
```


Downloading the application to see the structure, can find the file install.php, the file take to the update.php file
![[Pasted image 20211105023943.png]]

![[Pasted image 20211105024111.png]]

### /admin.php
* Creds: admin:nibbles

![[Pasted image 20211105030406.png]]