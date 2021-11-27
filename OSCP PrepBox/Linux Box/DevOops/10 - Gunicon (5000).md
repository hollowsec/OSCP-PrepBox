# Web Server on 5000

![[Pasted image 20211127085256.png]]

```bash
$ ffuf -u http://10.10.10.91:5000/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.91:5000/FUZZ
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________

upload                  [Status: 200, Size: 347, Words: 44, Lines: 1]
feed                    [Status: 200, Size: 546263, Words: 1, Lines: 1]
```

![[Pasted image 20211127085337.png]]

![[Pasted image 20211127090656.png]]


* [Payload](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XXE%20Injection/Files/Classic%20XXE%20-%20etc%20passwd.xml)
![[Pasted image 20211127091013.png]]


*feed.py lfi
page newpost (POST), picklestr has vuln?
![[Pasted image 20211127091243.png]]

