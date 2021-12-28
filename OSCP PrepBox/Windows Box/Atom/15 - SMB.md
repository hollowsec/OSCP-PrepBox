```bash
$ smbclient -L //10.10.10.237/
Enter WORKGROUP\dix's password: 

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        Software_Updates Disk      
SMB1 disabled -- no workgroup availabl

```

```bash
$ smbclient //10.10.10.237/Software_Updates
Enter WORKGROUP\dix's password: 
Try "help" to get a list of possible commands.
smb: \> dir
  .                                   D        0  Sun Dec 19 01:45:57 2021
  ..                                  D        0  Sun Dec 19 01:45:57 2021
  client1                             D        0  Sun Dec 19 01:45:57 2021
  client2                             D        0  Sun Dec 19 01:45:57 2021
  client3                             D        0  Sun Dec 19 01:45:57 2021
  UAT_Testing_Procedures.pdf          A    35202  Fri Apr  9 08:18:08 2021

                4413951 blocks of size 4096. 1356730 blocks available
smb: \> get UAT_Testing_Procedures.pdf
getting file \UAT_Testing_Procedures.pdf of size 35202 as UAT_Testing_Procedures.pdf (40,3 KiloBytes/sec) (average 40,3 KiloBytes/sec)
smb: \> exit

```

* App build with electron
![[Pasted image 20211219004601.png]]