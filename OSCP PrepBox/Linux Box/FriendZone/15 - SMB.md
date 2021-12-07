```bash
$ smbmap -H 10.10.10.123 -s general                                                                                                                                                  
[+] Guest session       IP: 10.10.10.123:445    Name: friendzone.red                                                    
        Disk                                                    Permissions     Comment                                                                                                       
        ----                                                    -----------     -------                                                                                                       
        print$                                                  NO ACCESS       Printer Drivers                                                                                               
        Files                                                   NO ACCESS       FriendZone Samba Server Files /etc/Files
        general                                                 READ ONLY       FriendZone Samba Server Files                                                                                 
        Development                                             READ, WRITE     FriendZone Samba Server Files                                                                                 
        IPC$                                                    NO ACCESS       IPC Service (FriendZone server (Samba, Ubuntu))
```

```bash
smbmap -R general -H 10.10.10.123                                                                                                                                                  
[+] Guest session       IP: 10.10.10.123:445    Name: friendzone.red                                                                                                                          
        Disk                                                    Permissions     Comment                                                                                                       
        ----                                                    -----------     -------                                                                                                       
        general                                                 READ ONLY                                                                                                                     
        .\general\*                                                                                                                                                                           
        dr--r--r--                0 Wed Jan 16 18:10:51 2019    .                                                                                                                             
        dr--r--r--                0 Wed Jan 23 19:51:02 2019    ..                                                                                                                            
        fr--r--r--               57 Tue Oct  9 20:52:42 2018    creds.txt
```

```bash
$ smbclient  //10.10.10.123/general
```

```bash
smb: \> get creds.txt
getting file \creds.txt of size 57 as creds.txt (0,1 KiloBytes/sec) (average 0,1 KiloBytes/sec)
```

admin:WORKWORKHhallelujah@#
![[Pasted image 20211130083938.png]]

