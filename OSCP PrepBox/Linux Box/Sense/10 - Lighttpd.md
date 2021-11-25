# Web Server on 80

* PfSense
* **2.1.3-RELEASE ** (amd64)
* Creds: rohit:pfsense
Block bruteforce after 15 attempts

```bash
$ ffuf -u https://10.10.10.60/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-small-words.txt -mc 200,204,301,302,307 -e .txt -c

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : https://10.10.10.60/FUZZ
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-small-words.txt
 :: Extensions       : .txt 
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307
________________________________________________

themes                  [Status: 301, Size: 0, Words: 1, Lines: 1]
includes                [Status: 301, Size: 0, Words: 1, Lines: 1]
css                     [Status: 301, Size: 0, Words: 1, Lines: 1]
classes                 [Status: 301, Size: 0, Words: 1, Lines: 1]
javascript              [Status: 301, Size: 0, Words: 1, Lines: 1]
.                       [Status: 200, Size: 6690, Words: 907, Lines: 174]
widgets                 [Status: 301, Size: 0, Words: 1, Lines: 1]
installer               [Status: 301, Size: 0, Words: 1, Lines: 1]
tree                    [Status: 301, Size: 0, Words: 1, Lines: 1]
changelog.txt           [Status: 200, Size: 271, Words: 35, Lines: 10]
wizards                 [Status: 301, Size: 0, Words: 1, Lines: 1]
shortcuts               [Status: 301, Size: 0, Words: 1, Lines: 1]
:: Progress: [86006/86006] :: Job [1/1] :: 208 req/sec :: Duration: [0:13:39] :: Errors: 0 ::

```


