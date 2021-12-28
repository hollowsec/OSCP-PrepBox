# Homepage
![[Pasted image 20211220124105.png]]


* Warning telling is restricted login for our ip address http://10.10.10.228/portal/login.php
![[Pasted image 20211220124509.png]]

*  Trying to sign up, ignoring warning
![[Pasted image 20211220124803.png]]

* Can sign up and login 
![[Pasted image 20211220124843.png]]

### [Users List](http://10.10.10.228/portal/php/users.php)
![[Pasted image 20211220124957.png]]

### [Active Users](http://10.10.10.228/portal/php/admins.php)
![[Pasted image 20211220125627.png]]


###  [Issues](http://10.10.10.228/portal/php/issues.php)
![[Pasted image 20211220125733.png]]


* Passing FIleManagement to burpsuite and intercept response
* Change 302 FOund to 200 OK
![[Pasted image 20211220195458.png]]

### Upload Page
![[Pasted image 20211220195524.png]]



### Proxy the books action

![[Pasted image 20211220195626.png]]
![[Pasted image 20211220195651.png]]

* change book param, for a book its doens't exist
* output: path, lfi?
![[Pasted image 20211220195733.png]]

* file_contents bring the source file, doens't interpet php
* trying to get db.php
![[Pasted image 20211220200431.png]]

* ***Creds:bread:jUli901 ***

* Grabbing fileCOntroller.php (upload page)
* ***JWT Secret_key : 6cb9c1a2786a483ca5e44571dcc5f3bfa298593a6376ad92185c3258acd5591e ***
![[Pasted image 20211220201007.png]]

### Automate LFI and crawler script [[12 - LFI Script]]



