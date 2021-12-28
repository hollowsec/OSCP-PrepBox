# Nmap
```sql
# Nmap 7.92 scan initiated Mon Dec 20 12:35:43 2021 as: nmap -sC -sV -oA nmap/initial 10.10.10.228
Nmap scan report for 10.10.10.228
Host is up (0.24s latency).
Not shown: 993 closed tcp ports (reset)
PORT     STATE SERVICE       VERSION
22/tcp   open  ssh           OpenSSH for_Windows_7.7 (protocol 2.0)
| ssh-hostkey: 
|   2048 9d:d0:b8:81:55:54:ea:0f:89:b1:10:32:33:6a:a7:8f (RSA)
|   256 1f:2e:67:37:1a:b8:91:1d:5c:31:59:c7:c6:df:14:1d (ECDSA)
|_  256 30:9e:5d:12:e3:c6:b7:c6:3b:7e:1e:e7:89:7e:83:e4 (ED25519)
80/tcp   open  http          Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1h PHP/8.0.1)
|_http-title: Library
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1h PHP/8.0.1
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
443/tcp  open  ssl/http      Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1h PHP/8.0.1)
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-title: Library
| tls-alpn: 
|_  http/1.1
|_ssl-date: TLS randomness does not represent time
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1h PHP/8.0.1
| ssl-cert: Subject: commonName=localhost
| Not valid before: 2009-11-10T23:48:47
|_Not valid after:  2019-11-08T23:48:47
445/tcp  open  microsoft-ds?
3306/tcp open  mysql?
| fingerprint-strings: 
|   DNSVersionBindReqTCP, Kerberos, LANDesk-RC, NotesRPC, RTSPRequest, SMBProgNeg, SSLSessionReq, TLSSessionReq, TerminalServerCookie, WMSRequest, oracle-tns: 
|_    Host '10.10.14.21' is not allowed to connect to this MariaDB server
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.92%I=7%D=12/20%Time=61C0A2E5%P=x86_64-pc-linux-gnu%r(R
SF:TSPRequest,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\
SF:x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(DNSV
SF:ersionBindReqTCP,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x
SF:20not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%
SF:r(SSLSessionReq,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x2
SF:0not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r
SF:(TerminalServerCookie,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x2
SF:0is\x20not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20serv
SF:er")%r(TLSSessionReq,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20
SF:is\x20not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20serve
SF:r")%r(Kerberos,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20
SF:not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(
SF:SMBProgNeg,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\
SF:x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(LAND
SF:esk-RC,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20a
SF:llowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(NotesRPC
SF:,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed
SF:\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(WMSRequest,4A,
SF:"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20
SF:to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(oracle-tns,4A,"F\0
SF:\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x
SF:20connect\x20to\x20this\x20MariaDB\x20server");
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2021-12-20T15:42:55
|_  start_date: N/A
| smb2-security-mode: 
|   3.1.1: 
|_    Message signing enabled but not required
|_clock-skew: 6m32s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Dec 20 12:36:32 2021 -- 1 IP address (1 host up) scanned in 49.30 seconds

```

```bash
$ ffuf -u http://10.10.10.228/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt -c -e .php                                                                 
                                                                                                                                                                                              
        /'___\  /'___\           /'___\                                                                                                                                                       
       /\ \__/ /\ \__/  __  __  /\ \__/                                                        
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                       
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                       
         \ \_\   \ \_\  \ \____/  \ \_\                                                        
          \/_/    \/_/   \/___/    \/_/                                                        
                                                                                               
       v1.3.1 Kali Exclusive <3                                                                
________________________________________________                      
                                                                                               
 :: Method           : GET                                                                     
 :: URL              : http://10.10.10.228/FUZZ                       
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt
 :: Extensions       : .php                                                                    
 :: Follow redirects : false                                                                   
 :: Calibration      : false                                                                   
 :: Timeout          : 10                                                                      
 :: Threads          : 40                                                                      
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________                      
                                                                                               
index.php               [Status: 200, Size: 2368, Words: 447, Lines: 46]
.htm                    [Status: 403, Size: 301, Words: 22, Lines: 10]
.htm.php                [Status: 403, Size: 301, Words: 22, Lines: 10]
.html.php               [Status: 403, Size: 301, Words: 22, Lines: 10]
.html                   [Status: 403, Size: 301, Words: 22, Lines: 10]
js                      [Status: 301, Size: 333, Words: 22, Lines: 10]
includes                [Status: 301, Size: 339, Words: 22, Lines: 10]
css                     [Status: 301, Size: 334, Words: 22, Lines: 10]
db                      [Status: 301, Size: 333, Words: 22, Lines: 10]
php                     [Status: 301, Size: 334, Words: 22, Lines: 10]
webalizer               [Status: 403, Size: 301, Words: 22, Lines: 10]
.                       [Status: 200, Size: 2368, Words: 447, Lines: 46]
portal                  [Status: 301, Size: 337, Words: 22, Lines: 10]
phpmyadmin              [Status: 403, Size: 301, Words: 22, Lines: 10]
.htaccess               [Status: 403, Size: 301, Words: 22, Lines: 10]
.htaccess.php           [Status: 403, Size: 301, Words: 22, Lines: 10]
books                   [Status: 301, Size: 336, Words: 22, Lines: 10
```