# Nmap

```bash
$ sudo nmap -p- -oA nmap/allports 10.10.10.187
Starting Nmap 7.92 ( https://nmap.org ) at 2021-12-06 08:48 -03
Nmap scan report for 10.10.10.187
Host is up (0.18s latency).
Not shown: 65532 closed tcp ports (reset)
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 705.35 seconds\
```

# ffuf
```bash
$ ffuf -u http://10.10.10.187/admin-dir/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c -e .php,.txt                                                            
                                                                                               
        /'___\  /'___\           /'___\                                                        
       /\ \__/ /\ \__/  __  __  /\ \__/                                                        
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                       
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                       
         \ \_\   \ \_\  \ \____/  \ \_\                                                        
          \/_/    \/_/   \/___/    \/_/                                                        
                                                                                               
       v1.3.1 Kali Exclusive <3                                                                
________________________________________________                      
                                                                                               
 :: Method           : GET                                                                     
 :: URL              : http://10.10.10.187/admin-dir/FUZZ             
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Extensions       : .php .txt                                                               
 :: Follow redirects : false                                                                   
 :: Calibration      : false                                                                   
 :: Timeout          : 10                                                                      
 :: Threads          : 40                                                                      
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________                      
                                                                                               
.html.php               [Status: 403, Size: 277, Words: 20, Lines: 10]
.php                    [Status: 403, Size: 277, Words: 20, Lines: 10]
.html                   [Status: 403, Size: 277, Words: 20, Lines: 10]
.htm                    [Status: 403, Size: 277, Words: 20, Lines: 10]
.htm.php                [Status: 403, Size: 277, Words: 20, Lines: 10]
.html.txt               [Status: 403, Size: 277, Words: 20, Lines: 10]
.htm.txt                [Status: 403, Size: 277, Words: 20, Lines: 10]                                                                                                                        
contacts.txt            [Status: 200, Size: 350, Words: 19, Lines: 30]
.                       [Status: 403, Size: 277, Words: 20, Lines: 10]
.htaccess               [Status: 403, Size: 277, Words: 20, Lines: 10]
.htaccess.php           [Status: 403, Size: 277, Words: 20, Lines: 10]
.htaccess.txt           [Status: 403, Size: 277, Words: 20, Lines: 10]
.php3                   [Status: 403, Size: 277, Words: 20, Lines: 10]
.phtml                  [Status: 403, Size: 277, Words: 20, Lines: 10]
.htc                    [Status: 403, Size: 277, Words: 20, Lines: 10]
.htc.php                [Status: 403, Size: 277, Words: 20, Lines: 10]
.ht.php                 [Status: 403, Size: 277, Words: 20, Lines: 10]
.ht.txt                 [Status: 403, Size: 277, Words: 20, Lines: 10]
.html.bak               [Status: 403, Size: 277, Words: 20, Lines: 10]
.html.bak.php           [Status: 403, Size: 277, Words: 20, Lines: 10]                                                                                                                        
.html.bak.txt           [Status: 403, Size: 277, Words: 20, Lines: 10]
credentials.txt         [Status: 200, Size: 136, Words: 5, Lines: 12] 
.htm.htm                [Status: 403, Size: 277, Words: 20, Lines: 10]
.htm.htm.php            [Status: 403, Size: 277, Words: 20, Lines: 10]
.htm.htm.txt            [Status: 403, Size: 277, Words: 20, Lines: 10]
.hta                    [Status: 403, Size: 277, Words: 20, Lines: 10]
.hta.php                [Status: 403, Size: 277, Words: 20, Lines: 10]
```

