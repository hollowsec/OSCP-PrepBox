# Nmap
```bash
$ sudo nmap -sC -sV -oA nmap/initial 10.10.10.143
[sudo] password for dix: 
Starting Nmap 7.92 ( https://nmap.org ) at 2021-12-03 11:14 -03
Nmap scan report for 10.10.10.143
Host is up (0.17s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.4p1 Debian 10+deb9u6 (protocol 2.0)
| ssh-hostkey: 
|   2048 03:f3:4e:22:36:3e:3b:81:30:79:ed:49:67:65:16:67 (RSA)
|   256 25:d8:08:a8:4d:6d:e8:d2:f8:43:4a:2c:20:c8:5a:f6 (ECDSA)
|_  256 77:d4:ae:1f:b0:be:15:1f:f8:cd:c8:15:3a:c3:69:e1 (ED25519)
80/tcp open  http    Apache httpd 2.4.25 ((Debian))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-title: Stark Hotel
|_http-server-header: Apache/2.4.25 (Debian)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 17.35 seconds
```

allports

```bash
$ sudo nmap -p- -oA nmap/allports 10.10.10.143
[sudo] password for dix: 
Starting Nmap 7.92 ( https://nmap.org ) at 2021-12-03 11:14 -03
Nmap scan report for 10.10.10.143
Host is up (0.18s latency).
Not shown: 65532 closed tcp ports (reset)
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
64999/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 346.04 seconds
```


# ffuf
## Directory Brute Force
```bash
$ ffuf -u http://10.10.10.143/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c -e .php
\                                                                                              
        /'___\  /'___\           /'___\                                                        
       /\ \__/ /\ \__/  __  __  /\ \__/                                                        
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                       
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                       
         \ \_\   \ \_\  \ \____/  \ \_\                                                        
          \/_/    \/_/   \/___/    \/_/                                                        
                                                                                               
       v1.3.1 Kali Exclusive <3                                                                
________________________________________________                      
                                                                                               
 :: Method           : GET                                                                     
 :: URL              : http://10.10.10.143/FUZZ                         
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Extensions       : .php                                                                    
 :: Follow redirects : false                                                                   
 :: Calibration      : false                                                                   
 :: Timeout          : 10                                                                      
 :: Threads          : 40                                                                      
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________                      
                                                                                               
index.php               [Status: 200, Size: 23628, Words: 3014, Lines: 544]
.php                    [Status: 403, Size: 291, Words: 22, Lines: 12]
.html                   [Status: 403, Size: 292, Words: 22, Lines: 12]
.htm                    [Status: 403, Size: 291, Words: 22, Lines: 12]
.htm.php                [Status: 403, Size: 295, Words: 22, Lines: 12]
images                  [Status: 301, Size: 313, Words: 20, Lines: 10]
css                     [Status: 301, Size: 310, Words: 20, Lines: 10]
js                      [Status: 301, Size: 309, Words: 20, Lines: 10]   
.html.php               [Status: 403, Size: 296, Words: 22, Lines: 12]
footer.php              [Status: 200, Size: 2237, Words: 101, Lines: 69]
.                       [Status: 200, Size: 23628, Words: 3014, Lines: 544]
fonts                   [Status: 301, Size: 312, Words: 20, Lines: 10]
phpmyadmin              [Status: 301, Size: 317, Words: 20, Lines: 10]
.htaccess               [Status: 403, Size: 296, Words: 22, Lines: 12]
.htaccess.php           [Status: 403, Size: 300, Words: 22, Lines: 12]
nav.php                 [Status: 200, Size: 1333, Words: 76, Lines: 44
```

