# Nmap

```bash
# Nmap 7.92 scan initiated Wed Dec  8 16:03:42 2021 as: nmap -sC -sV -oA nmap/initial 10.10.10.191
Nmap scan report for 10.10.10.191
Host is up (0.18s latency).
Scanned at 2021-12-08 16:03:43 -03 for 39s
Not shown: 998 filtered tcp ports (no-response)
PORT   STATE  SERVICE VERSION
21/tcp closed ftp
80/tcp open   http    Apache httpd 2.4.41 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-generator: Blunder
|_http-favicon: Unknown favicon MD5: A0F0E5D852F0E3783AF700B6EE9D00DA
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Blunder | A blunder of interesting facts
```


# ffuf
```bash

$ ffuf -u http://10.10.10.191/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c -e .php,.txt -mc 200,204,301,302,307,401,405

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.191/FUZZ
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Extensions       : .php .txt 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,405
________________________________________________

install.php             [Status: 200, Size: 30, Words: 5, Lines: 1]
admin                   [Status: 301, Size: 0, Words: 1, Lines: 1]
LICENSE                 [Status: 200, Size: 1083, Words: 155, Lines: 22]
about                   [Status: 200, Size: 3281, Words: 225, Lines: 106]
0                       [Status: 200, Size: 7562, Words: 794, Lines: 171]
robots.txt              [Status: 200, Size: 22, Words: 3, Lines: 2]
todo.txt                [Status: 200, Size: 118, Words: 20, Lines: 5]
usb                     [Status: 200, Size: 3960, Words: 304, Lines: 111]
.gitignore              [Status: 200, Size: 563, Words: 1, Lines: 28]
```



