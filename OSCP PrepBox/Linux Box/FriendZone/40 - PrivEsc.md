# Getting Root
```bash
www-data@FriendZone:/var/www$ ls -la
total 36
drwxr-xr-x  8 root root 4096 Oct  6  2018 .
drwxr-xr-x 12 root root 4096 Oct  6  2018 ..
drwxr-xr-x  3 root root 4096 Jan 16  2019 admin
drwxr-xr-x  4 root root 4096 Oct  6  2018 friendzone
drwxr-xr-x  2 root root 4096 Oct  6  2018 friendzoneportal
drwxr-xr-x  2 root root 4096 Jan 15  2019 friendzoneportaladmin
drwxr-xr-x  3 root root 4096 Oct  6  2018 html
-rw-r--r--  1 root root  116 Oct  6  2018 mysql_data.conf
drwxr-xr-x  3 root root 4096 Oct  6  2018 uploads
www-data@FriendZone:/var/www$ car mysql_data.conf
```

```bash
cat mysql_data.conf 
for development process this is the mysql creds for user friend

db_user=friend

db_pass=Agpyu12!0.213$

db_name=FZ
```
Dont have any port of database open, no 3306 (mysql)
![[Pasted image 20211130125844.png]]

Trying to use the creds to login as friend
![[Pasted image 20211130130129.png]]

Can login as friend on SSH too
![[Pasted image 20211130130332.png]]

Script runnig on system
![[Pasted image 20211130143619.png]]

Run linpeas on machine, found  writeable file os.py (python library). Script report.py call library 'os'
![[Pasted image 20211130132316.png]]

```bash
/dev/shm$ vi /usr/lib/python2.7/os.py
```
![[Pasted image 20211130155836.png]]


![[Pasted image 20211130155918.png]]