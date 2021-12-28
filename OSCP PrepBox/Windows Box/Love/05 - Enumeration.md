# Nmap
```sql
# Nmap 7.92 scan initiated Thu Dec 23 16:00:24 2021 as: nmap -sC -sV -oA nmap/initial 10.10.10.239
Nmap scan report for 10.10.10.239
Host is up (0.16s latency).
Not shown: 993 closed tcp ports (reset)
PORT     STATE SERVICE      VERSION
80/tcp   open  http         Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1j PHP/7.3.27)
|_http-title: Voting System using PHP
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
135/tcp  open  msrpc        Microsoft Windows RPC
139/tcp  open  netbios-ssn  Microsoft Windows netbios-ssn
443/tcp  open  ssl/http     Apache httpd 2.4.46 (OpenSSL/1.1.1j PHP/7.3.27)
|_http-title: 403 Forbidden
| tls-alpn: 
|_  http/1.1
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=staging.love.htb/organizationName=ValentineCorp/stateOrProvinceName=m/countryName=in
| Not valid before: 2021-01-18T14:00:16
|_Not valid after:  2022-01-18T14:00:16
445/tcp  open  microsoft-ds Windows 10 Pro 19042 microsoft-ds (workgroup: WORKGROUP)
3306/tcp open  mysql?
| fingerprint-strings: 
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, GetRequest, Help, Kerberos, LANDesk-RC, LDAPBindReq, LDAPSearchReq, LPDString, RPCCheck, SIPOptions, SMBProgNeg, TerminalServer, TerminalServerCookie, X11Probe: 
|_    Host '10.10.14.21' is not allowed to connect to this MariaDB server
5000/tcp open  http         Apache httpd 2.4.46 (OpenSSL/1.1.1j PHP/7.3.27)
|_http-title: 403 Forbidden
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1j PHP/7.3.27
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.92%I=7%D=12/23%Time=61C4C76E%P=x86_64-pc-linux-gnu%r(G
SF:etRequest,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x
SF:20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(RPCCh
SF:eck,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allo
SF:wed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(DNSVersionB
SF:indReqTCP,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x
SF:20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(DNSSt
SF:atusRequestTCP,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20
SF:not\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(
SF:Help,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20all
SF:owed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(TerminalSe
SF:rverCookie,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\
SF:x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(Kerb
SF:eros,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20all
SF:owed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(SMBProgNeg
SF:,4A,"F\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed
SF:\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(X11Probe,4A,"F
SF:\0\0\x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to
SF:\x20connect\x20to\x20this\x20MariaDB\x20server")%r(LPDString,4A,"F\0\0\
SF:x01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20c
SF:onnect\x20to\x20this\x20MariaDB\x20server")%r(LDAPSearchReq,4A,"F\0\0\x
SF:01\xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20co
SF:nnect\x20to\x20this\x20MariaDB\x20server")%r(LDAPBindReq,4A,"F\0\0\x01\
SF:xffj\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20conne
SF:ct\x20to\x20this\x20MariaDB\x20server")%r(SIPOptions,4A,"F\0\0\x01\xffj
SF:\x04Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20connect\x
SF:20to\x20this\x20MariaDB\x20server")%r(LANDesk-RC,4A,"F\0\0\x01\xffj\x04
SF:Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20connect\x20to
SF:\x20this\x20MariaDB\x20server")%r(TerminalServer,4A,"F\0\0\x01\xffj\x04
SF:Host\x20'10\.10\.14\.21'\x20is\x20not\x20allowed\x20to\x20connect\x20to
SF:\x20this\x20MariaDB\x20server");
Service Info: Hosts: www.example.com, LOVE, www.love.htb; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-time: 
|   date: 2021-12-23T20:29:28
|_  start_date: N/A
| smb2-security-mode: 
|   3.1.1: 
|_    Message signing enabled but not required
| smb-os-discovery: 
|   OS: Windows 10 Pro 19042 (Windows 10 Pro 6.3)
|   OS CPE: cpe:/o:microsoft:windows_10::-
|   Computer name: Love
|   NetBIOS computer name: LOVE\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2021-12-23T12:29:23-08:00
|_clock-skew: mean: 4h08m07s, deviation: 4h37m08s, median: 1h28m06s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Dec 23 16:01:31 2021 -- 1 IP address (1 host up) scanned in 67.29 seconds

```

### Allports
```sql
$ sudo nmap -p- -oA nmap/allports 10.10.10.239
[sudo] password for dix: 
Starting Nmap 7.92 ( https://nmap.org ) at 2021-12-23 21:38 -03
Nmap scan report for 10.10.10.239
Host is up (0.17s latency).
Not shown: 65516 closed tcp ports (reset)
PORT      STATE SERVICE
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
3306/tcp  open  mysql
5000/tcp  open  upnp
5040/tcp  open  unknown
5985/tcp  open  wsman
5986/tcp  open  wsmans
7680/tcp  open  pando-pub
47001/tcp open  winrm
49664/tcp open  unknown
49665/tcp open  unknown
49666/tcp open  unknown
49667/tcp open  unknown
49668/tcp open  unknown
49669/tcp open  unknown
49670/tcp open  unknown
```

# ffuf
```bash
$ ffuf -u http://10.10.10.239/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt -c                                                                         
                                                                                                                                                                                              
        /'___\  /'___\           /'___\                                                                                                                                                       
       /\ \__/ /\ \__/  __  __  /\ \__/                                                                                                                                                       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                                                                                                                      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                                                                                                                      
         \ \_\   \ \_\  \ \____/  \ \_\                                                                                                                                                       
          \/_/    \/_/   \/___/    \/_/                                                                                                                                                       

       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.239/FUZZ 
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words-lowercase.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

images                  [Status: 301, Size: 338, Words: 22, Lines: 10]
admin                   [Status: 301, Size: 337, Words: 22, Lines: 10]
includes                [Status: 301, Size: 340, Words: 22, Lines: 10]
.html                   [Status: 403, Size: 302, Words: 22, Lines: 10]
.htm                    [Status: 403, Size: 302, Words: 22, Lines: 10]
plugins                 [Status: 301, Size: 339, Words: 22, Lines: 10]
webalizer               [Status: 403, Size: 302, Words: 22, Lines: 10]
.                       [Status: 200, Size: 4388, Words: 654, Lines: 126]
phpmyadmin              [Status: 403, Size: 302, Words: 22, Lines: 10]
.htaccess               [Status: 403, Size: 302, Words: 22, Lines: 10]
.htc                    [Status: 403, Size: 302, Words: 22, Lines: 10]
dist                    [Status: 301, Size: 336, Words: 22, Lines: 10]
.html_var_de            [Status: 403, Size: 302, Words: 22, Lines: 10]
licenses                [Status: 403, Size: 421, Words: 37, Lines: 12]
server-status           [Status: 403, Size: 421, Words: 37, Lines: 12]
.htpasswd               [Status: 403, Size: 302, Words: 22, Lines: 10]
con                     [Status: 403, Size: 302, Words: 22, Lines: 10]
tcpdf                   [Status: 301, Size: 337, Words: 22, Lines: 10]
.html.                  [Status: 403, Size: 302, Words: 22, Lines: 10]
.html.html              [Status: 403, Size: 302, Words: 22, Lines: 10]
.htpasswds              [Status: 403, Size: 302, Words: 22, Lines: 10]

```
