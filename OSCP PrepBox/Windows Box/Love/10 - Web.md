# Certificate https
![[Pasted image 20211223214649.png]]



# Homepage
http://love.htb/
![[Pasted image 20211223215039.png]]


### Staging.love
http://staging.love.htb/
![[Pasted image 20211223215106.png]]

### admin
 http://love.htb/admin/

![[Pasted image 20211225214335.png]]




### Trying to SSRF on [beta.php](http://staging.love.htb/beta.php)
* Retrieve info about the port 5000 , using the server itself. On our machine we receive 403 forbideen.
* Input: http://127.0.0.1:5000 
* Output:
** Vote Admin Creds admin: @LoveIsInTheAir!!!! **
![[Pasted image 20211225215149.png]]


### login on love.htb/admin
using Creds: admin:@LoveIsInTheAir!!!! 
![[Pasted image 20211226122917.png]]

