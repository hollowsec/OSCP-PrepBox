# Nmap 
```bash
22/tcp  open   ssh     OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 22:75:d7:a7:4f:81:a7:af:52:66:e5:27:44:b1:01:5b (RSA)
|   256 2d:63:28:fc:a2:99:c7:d4:35:b9:45:9a:4b:38:f9:c8 (ECDSA)
|_  256 73:cd:a0:5b:84:10:7d:a7:1c:7c:61:1d:f5:54:cf:c4 (ED25519)
80/tcp  open   http    Apache httpd 2.4.6 ((CentOS) PHP/5.4.16)
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
|_http-server-header: Apache/2.4.6 (CentOS) PHP/5.4.16
443/tcp closed https
```

# Fuff

```bash
$ ffuf  -u http://10.10.10.146/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c -e .php                                                                          
                                                                                                                                                                                              
        /'___\  /'___\           /'___\                                                        
       /\ \__/ /\ \__/  __  __  /\ \__/                                                        
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                       
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                       
         \ \_\   \ \_\  \ \____/  \ \_\                                                        
          \/_/    \/_/   \/___/    \/_/                                                        
                                                                                               
       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.146/FUZZ 
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Extensions       : .php 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

.html                   [Status: 403, Size: 207, Words: 15, Lines: 9]
.htm                    [Status: 403, Size: 206, Words: 15, Lines: 9]
.htm.php                [Status: 403, Size: 210, Words: 15, Lines: 9]
index.php               [Status: 200, Size: 229, Words: 33, Lines: 9]
lib.php                 [Status: 200, Size: 0, Words: 1, Lines: 1]
uploads                 [Status: 301, Size: 236, Words: 14, Lines: 8]
backup                  [Status: 301, Size: 235, Words: 14, Lines: 8]
upload.php              [Status: 200, Size: 169, Words: 11, Lines: 6]
.html.php               [Status: 403, Size: 211, Words: 15, Lines: 9]
photos.php              [Status: 200, Size: 1302, Words: 68, Lines: 23]
.                       [Status: 200, Size: 229, Words: 33, Lines: 9]
```