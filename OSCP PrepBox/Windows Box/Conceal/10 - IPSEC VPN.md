# IPSEC 
configure IPsec
```bash
$ sudo vim /etc/ipsec.secrets
```

![[Pasted image 20211128123849.png]]

```bash
$ sudo vim /etc/ipsec.conf
```

 ![[Pasted image 20211129025819.png]]
 
 ```bash
 $ sudo ipsec restart --nofork 
 ```
 Now can scan the tcp ports and receive ports open
 
 ```bash
 PORT    STATE SERVICE       VERSION                                                            
21/tcp  open  ftp           Microsoft ftpd
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)                                         
| ftp-syst:                                    
|_  SYST: Windows_NT 
80/tcp  open  http          Microsoft IIS httpd 10.0                                           
|_http-server-header: Microsoft-IIS/10.0       
|_http-title: IIS Windows                                                                      
| http-methods:                                                                                
|   Supported Methods: OPTIONS TRACE GET HEAD POST                      
|_  Potentially risky methods: TRACE                                                           
135/tcp open  msrpc         Microsoft Windows RPC                                              
139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn        
445/tcp open  microsoft-ds?     
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows                                       
                                                                                               
Host script results:                                                                           
| smb2-time:                                                                                   
|   date: 2021-11-29T06:11:09     
|_  start_date: 2021-11-28T11:21:05
| smb2-security-mode:                                                                          
|   3.1.1:                            
|_    Message signing enabled but not required
|_clock-skew: 6m22s 
 ```