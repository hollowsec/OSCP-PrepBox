# Wordpress on 80

![[Pasted image 20211115014627.png]]

List of mail user fouind:
r.hilton@bart.htb
d.simmons@bart.htb
s.brown@bart.local
h.potter@bart.htb

Developer@BART

Harvey Potter
Daniella Lamborghini

```bash
$ ffuf -u http://10.10.10.81/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt -c -mc 204,301,302,307,401,403,405

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.3.1 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.10.81/FUZZ
 :: Wordlist         : FUZZ: /opt/SecLists/Discovery/Web-Content/raft-medium-words.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 204,301,302,307,401,403,405
________________________________________________

forum                   [Status: 301, Size: 148, Words: 9, Lines: 2]
.                       [Status: 302, Size: 0, Words: 1, Lines: 1]
:: Progress: [1335/63087] :: Job [1/1] :: 4 req/sec :: Duration: [0:05:39] :: Errors: 13 ::
[INFO] ------ PAUSING ------

entering interactive mode
type "help" for a list of commands, or ENTER to resume.
> 
[INFO] ------ RESUMING -----

Forum                   [Status: 301, Size: 148, Words: 9, Lines: 2]
monitor                 [Status: 301, Size: 150, Words: 9, Lines: 2]

```



http://bart.htb/monitor/
![[Pasted image 20211115015304.png]]



Give feedback to know if the user exists
![[Pasted image 20211115015456.png]]


Trying to use the users i found on main page

![[Pasted image 20211115020205.png]]

Creds: harvey:potter

![[Pasted image 20211115020602.png]]


![[Pasted image 20211115020911.png]]

![[Pasted image 20211115020930.png]]

```bash
$ hydra -h l harvey -P /usr/share/wordlists/rockyou.txt  internal-01.bart.htb http-form-post "/simple_chat/login.php:uname=^USER^&passwd=^PASS^&submit=Login:Password"
```

![[Pasted image 20211115023156.png]]
Creds: harvey:Password1

![[Pasted image 20211115024309.png]]

http://internal-01.bart.htb/log/log.php?filename=log.txt&username=harvey
![[Pasted image 20211115024642.png]]


![[Pasted image 20211115025733.png]]

![[Pasted image 20211115030102.png]]

Payload
![[Pasted image 20211115030412.png]]
![[Pasted image 20211115030507.png]]
