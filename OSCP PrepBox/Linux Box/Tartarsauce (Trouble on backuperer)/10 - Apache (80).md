# Web Server on 80
http://10.10.10.88/
![[Pasted image 20211111013902.png]]

![[Pasted image 20211111013932.png]]

http://10.10.10.88/webservices/monstra-3.0.4/
![[Pasted image 20211111014021.png]]


```bash

$ ffuf -u http://10.10.10.88/webservices/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c
                                                                                               
        /'___\  /'___\           /'___\                                                        
       /\ \__/ /\ \__/  __  __  /\ \__/                                                        
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\                                                       
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/                                                       
         \ \_\   \ \_\  \ \____/  \ \_\                                                        
          \/_/    \/_/   \/___/    \/_/                                                        
                                                                                               
       v1.3.1 Kali Exclusive <3                                                                
________________________________________________                      
                                                                                               
 :: Method           : GET                                                                     
 :: URL              : http://10.10.10.88/webservices/FUZZ            
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Follow redirects : false                                                                   
 :: Calibration      : false                                                                   
 :: Timeout          : 10                                                                      
 :: Threads          : 40                                                                      
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405
________________________________________________                      
                                                                                               
.html                   [Status: 403, Size: 303, Words: 22, Lines: 12]
.php                    [Status: 403, Size: 302, Words: 22, Lines: 12]
.htm                    [Status: 403, Size: 302, Words: 22, Lines: 12]
.                       [Status: 403, Size: 298, Words: 22, Lines: 12]
.htaccess               [Status: 403, Size: 307, Words: 22, Lines: 12]
wp                      [Status: 301, Size: 319, Words: 20, Lines: 10]
.php3                   [Status: 403, Size: 303, Words: 22, Lines: 12]
.phtml                  [Status: 403, Size: 304, Words: 22, Lines: 12]
.htc                    [Status: 403, Size: 302, Words: 22, Lines: 12]
.php5                   [Status: 403, Size: 303, Words: 22, Lines: 12]
```


![[Pasted image 20211111015839.png]]



### Monstra 3.0.4

Default Creds: admin:admin
![[Pasted image 20211111021445.png]]
![[Pasted image 20211111021515.png]]


