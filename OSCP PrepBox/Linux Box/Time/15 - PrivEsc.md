# LinPeas:

* sudo version: 1.8.31 Not vul ran : sudoedit -s '\\'\` perl -e 'print "A" x 65536'\`
* SystemD Timer: Wed 2021-12-15 04:46:51 UTC 2s left       Wed 2021-12-15 04:46:41 UTC 7s ago               timer_backup.timer           timer_backup.service
* You own the script: /usr/bin/timer_backup.sh 

## Priv Esc Chain

### TImer Backuo runs every 10s
```bash
pericles@time:/etc$ cat ./systemd/system/timer_backup.timer                                                                                                                                   
[Unit]                                                                                                                                                                                        
Description=Backup of the website                                                                                                                                                             
Requires=timer_backup.service                                                                                                                                                                 
                                                                                                                                                                                              
[Timer]                                                                                                                                                                                       
Unit=timer_backup.service                                                                                                                                                                     
#OnBootSec=10s                                                                                                                                                                                
#OnUnitActiveSec=10s                                                                                                                                                                          
OnUnitInactiveSec=10s                                                                                                                                                                         
AccuracySec=1ms                                                                                                                                                                               
                                                                                                                                                                                              
[Install]                                                                                                                                                                                     
WantedBy=timers.target                                                                                                                                                                        
pericles@time:/etc$ cat ./systemd/system/timer_backup.service                                                                                                                                 
[Unit]                                                                                                                                                                                        
Description=Calls website backup                                                                                                                                                              
Wants=timer_backup.timer                                                                                                                                                                      
WantedBy=multi-user.target
```

### Timer Backup calls web_backup.service
```bash
cat systemd/system/timer_backup.service
[Unit]
Description=Calls website backup
Wants=timer_backup.timer
WantedBy=multi-user.target

[Service]
ExecStart=/usr/bin/systemctl restart web_backup.service

```

### Web_backup executes /usr/bin/timer_backup.sh
```bash
pericles@time:/etc$ cat ./systemd/system/web_backup.service
[Unit]
Description=Creates backups of the website

[Service]
ExecStart=/bin/bash /usr/bin/timer_backup.sh
```

### Owned by pericles and world writable
```bash
pericles@time:/etc$ ls -la /usr/bin/timer_backup.sh
-rwxrw-rw- 1 pericles pericles 88 Dec 15 05:25 /usr/bin/timer_backup.sh
```

### Addiotionally, in /usr/bin/ but no placed by apt
```bash
pericles@time:/etc$ stat /usr/bin/timer_backup.sh
  File: /usr/bin/timer_backup.sh
  Size: 88              Blocks: 8          IO Block: 4096   regular file
Device: 802h/2050d      Inode: 1317302     Links: 1
Access: (0766/-rwxrw-rw-)  Uid: ( 1000/pericles)   Gid: ( 1000/pericles)
Access: 2021-12-15 05:25:01.068378202 +0000
Modify: 2021-12-15 05:25:01.052378202 +0000
Change: 2021-12-15 05:25:01.056378202 +0000
 Birth: -

```