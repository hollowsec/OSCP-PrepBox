# Nmap
```bash
PORT    STATE SERVICE  VERSION
80/tcp  open  http     Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
443/tcp open  ssl/http Apache httpd 2.4.18 ((Ubuntu))
| ssl-cert: Subject: commonName=nineveh.htb/organizationName=HackTheBox Ltd/stateOrProvinceName=Athens/countryName=GR
| Not valid before: 2017-07-01T15:03:30
|_Not valid after:  2018-07-01T15:03:30
|_ssl-date: TLS randomness does not represent time
|_http-server-header: Apache/2.4.18 (Ubuntu)
| tls-alpn: 
|_  http/1.1
|_http-title: Site doesn't have a title (text/html).

```

email:admin@nineveh.htb
![[Pasted image 20211109055045.png]]

```bash
$ ffuf -u https://nineveh.htb/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c                                                                                   
                                                                                               
        /'___\  /'___\           /'___\                                                        
       /\ \__/ /\ \__/  __  __  /\ \__/                                                        
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                       
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                       
         \ \_\   \ \_\  \ \____/  \ \_\                                                        
          \/_/    \/_/   \/___/    \/_/                                                        
                                                                                               
       v1.3.1 Kali Exclusive <3                                                                
________________________________________________                      
                                                                                               
 :: Method           : GET                                                                     
 :: URL              : https://nineveh.htb/FUZZ                       
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Follow redirects : false                                                                   
 :: Calibration      : false                                                                   
 :: Timeout          : 10                                                                      
 :: Threads          : 40                                                                      
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________                      
                                                                                               
.php                    [Status: 403, Size: 291, Words: 22, Lines: 12]
.html                   [Status: 403, Size: 292, Words: 22, Lines: 12]
.htm                    [Status: 403, Size: 291, Words: 22, Lines: 12]
db                      [Status: 301, Size: 309, Words: 20, Lines: 10]
.                       [Status: 200, Size: 49, Words: 3, Lines: 2]   
.htaccess               [Status: 403, Size: 296, Words: 22, Lines: 12]
.php3                   [Status: 403, Size: 292, Words: 22, Lines: 12]
.phtml                  [Status: 403, Size: 293, Words: 22, Lines: 12]
```


```bash
$ ffuf -u http://nineveh.htb/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c                                                                                 
                                                                                               
        /'___\  /'___\           /'___\                                                        
       /\ \__/ /\ \__/  __  __  /\ \__/                                                        
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                       
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                       
         \ \_\   \ \_\  \ \____/  \ \_\                                                        
          \/_/    \/_/   \/___/    \/_/                                                        
                                                                                               
       v1.3.1 Kali Exclusive <3                                                                
________________________________________________                                               
                                                                                               
 :: Method           : GET                                                                     
 :: URL              : http://nineveh.htb/FUZZ                                                 
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt         
 :: Follow redirects : false                                                                   
 :: Calibration      : false                                                                   
 :: Timeout          : 10                                                                      
 :: Threads          : 40                                                                      
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405                        
________________________________________________                                               
                                                                                               
.php                    [Status: 403, Size: 290, Words: 22, Lines: 12]                         
.html                   [Status: 403, Size: 291, Words: 22, Lines: 12]                         
.htm                    [Status: 403, Size: 290, Words: 22, Lines: 12]                         
.                       [Status: 200, Size: 178, Words: 22, Lines: 6]                          
.htaccess               [Status: 403, Size: 295, Words: 22, Lines: 12]                         
.php3                   [Status: 403, Size: 291, Words: 22, Lines: 12]                         
.phtml                  [Status: 403, Size: 292, Words: 22, Lines: 12]                         
.htc                    [Status: 403, Size: 290, Words: 22, Lines: 12]                         
.php5                   [Status: 403, Size: 291, Words: 22, Lines: 12]                         
.html_var_DE            [Status: 403, Size: 298, Words: 22, Lines: 12]                         
.php4                   [Status: 403, Size: 291, Words: 22, Lines: 12]                         
server-status           [Status: 403, Size: 299, Words: 22, Lines: 12]                         
.htpasswd               [Status: 403, Size: 295, Words: 22, Lines: 12]                         
department              [Status: 301, Size: 315, Words: 20, Lines: 10]                         
.html.                  [Status: 403, Size: 292, Words: 22, Lines: 12]
```

