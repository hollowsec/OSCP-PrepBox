# Nmap
```bash
PORT      STATE SERVICE           REASON          VERSION                                                                                                                                     
53/tcp    open  domain            syn-ack ttl 127 Microsoft DNS 6.1.7601 (1DB15D39) (Windows Server 2008 R2 SP1)                                                                              
| dns-nsid:                                                                                                                                                                                   
|_  bind.version: Microsoft DNS 6.1.7601 (1DB15D39)                                                                                                                                           
88/tcp    open  kerberos-sec      syn-ack ttl 127 Microsoft Windows Kerberos (server time: 2021-11-18 07:01:13Z)                                                                              
135/tcp   open  msrpc             syn-ack ttl 127 Microsoft Windows RPC                                                                                                                       
139/tcp   open  netbios-ssn       syn-ack ttl 127 Microsoft Windows netbios-ssn                                                                                                               
389/tcp   open  ldap              syn-ack ttl 127 Microsoft Windows Active Directory LDAP (Domain: active.htb, Site: Default-First-Site-Name)                                                 
445/tcp   open  microsoft-ds?     syn-ack ttl 127                                                                                                                                             
464/tcp   open  kpasswd5?         syn-ack ttl 127                                                                                                                                             
593/tcp   open  ncacn_http        syn-ack ttl 127 Microsoft Windows RPC over HTTP 1.0                                                                                                         
636/tcp   open  tcpwrapped        syn-ack ttl 127                                              
3268/tcp  open  ldap              syn-ack ttl 127 Microsoft Windows Active Directory LDAP (Domain: active.htb, Site: Default-First-Site-Name)
3269/tcp  open  globalcatLDAPssl? syn-ack ttl 127
49152/tcp open  msrpc             syn-ack ttl 127 Microsoft Windows RPC
49153/tcp open  msrpc             syn-ack ttl 127 Microsoft Windows RPC
49154/tcp open  msrpc             syn-ack ttl 127 Microsoft Windows RPC
49155/tcp open  msrpc             syn-ack ttl 127 Microsoft Windows RPC
49157/tcp open  ncacn_http        syn-ack ttl 127 Microsoft Windows RPC over HTTP 1.0
49158/tcp open  msrpc             syn-ack ttl 127 Microsoft Windows RPC
Service Info: Host: DC; OS: Windows; CPE: cpe:/o:microsoft:windows_server_2008:r2:sp1, cpe:/o:microsoft:windows

Host script results:
|_clock-skew: 6m30s
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 28591/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 40109/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 55960/udp): CLEAN (Timeout)
|   Check 4 (port 38631/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb2-time: 
|   date: 2021-11-18T07:02:17
|_  start_date: 2021-11-16T17:03:03
| smb2-security-mode: 
|   2.1: 
|_    Message signing enabled and required

```
Allports
```bash
PORT      STATE SERVICE                                                                                                                                                                       
53/tcp    open  domain                                                                                                                                                                        
88/tcp    open  kerberos-sec                                                                                                                                                                  
135/tcp   open  msrpc                                                                                                                                                                         
139/tcp   open  netbios-ssn                                                                                                                                                                   
389/tcp   open  ldap                                                                                                                                                                          
445/tcp   open  microsoft-ds                                                                                                                                                                  
464/tcp   open  kpasswd5                                                                                                                                                                      
593/tcp   open  http-rpc-epmap                                                                                                                                                                
636/tcp   open  ldapssl                                                                                                                                                                       
3268/tcp  open  globalcatLDAP                                                                                                                                                                 
3269/tcp  open  globalcatLDAPssl                                                                                                                                                              
5722/tcp  open  msdfsr                                                                                                                                                                        
9389/tcp  open  adws                                                                                                                                                                          
47001/tcp open  winrm                                                                                                                                                                         
49152/tcp open  unknown                                                                                                                                                                       
49153/tcp open  unknown                                                                                                                                                                       
49154/tcp open  unknown                                                                                                                                                                       
49155/tcp open  unknown                                                                                                                                                                       
49157/tcp open  unknown                                                                                                                                                                       
49158/tcp open  unknown                                                                                                                                                                       
49169/tcp open  unknown                                                                                                                                                                       
49172/tcp open  unknown                                                                                                                                                                       
49182/tcp open  unknow
```


# SMBMAP

```bash
$ smbmap -H 10.10.10.100                                                                                                                                                             
[+] IP: 10.10.10.100:445        Name: 10.10.10.100                                      
        Disk                                                    Permissions     Comment
        ----                                                    -----------     -------
        ADMIN$                                                  NO ACCESS       Remote Admin
        C$                                                      NO ACCESS       Default share
        IPC$                                                    NO ACCESS       Remote IPC
        NETLOGON                                                NO ACCESS       Logon server share 
        Replication                                             READ ONLY
        SYSVOL                                                  NO ACCESS       Logon server share 
        Users                                                   NO ACCESS

```



```bash

└──╼ [??]$ smbmap -R Replication  -H 10.10.10.100
[+] IP: 10.10.10.100:445        Name: 10.10.10.100
        Disk                                                    Permissions     Comment
        ----                                                    -----------     -------
        Replication                                             READ ONLY
        .\Replication\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    active.htb
        .\Replication\active.htb\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    DfsrPrivate
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Policies
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    scripts
        .\Replication\active.htb\DfsrPrivate\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ConflictAndDeleted
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Deleted
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Installing
        .\Replication\active.htb\Policies\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    {31B2F340-016D-11D2-945F-00C04FB984F9}
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    {6AC1786C-016F-11D2-945F-00C04fB984F9}
        .\Replication\active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        fr--r--r--               23 Sat Jul 21 07:38:11 2018    GPT.INI
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Group Policy
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    MACHINE
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    USER
        .\Replication\active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\Group Policy\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        fr--r--r--              119 Sat Jul 21 07:38:11 2018    GPE.INI
        .\Replication\active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\MACHINE\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Microsoft
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Preferences
        fr--r--r--             2788 Sat Jul 21 07:38:11 2018    Registry.pol
        .\Replication\active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\MACHINE\Microsoft\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Windows NT
        .\Replication\active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\MACHINE\Preferences\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Groups
        .\Replication\active.htb\Policies\{6AC1786C-016F-11D2-945F-00C04fB984F9}\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        fr--r--r--               22 Sat Jul 21 07:38:11 2018    GPT.INI
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    MACHINE
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    USER
        .\Rplication\active.htb\Policies\{6AC1786C-016F-11D2-945F-00C04fB984F9}\MACHINE\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Microsoft
        .\Replication\active.htb\Policies\{6AC1786C-016F-11D2-945F-00C04fB984F9}\MACHINE\Microsoft\*
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    .
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    ..
        dr--r--r--                0 Sat Jul 21 07:37:44 2018    Windows NT

```

* Groups.xml
![[Pasted image 20211124100317.png]]


![[Pasted image 20211124100446.png]]
** Creds:SVC_TGS:GPPstillStandingStrong2k18