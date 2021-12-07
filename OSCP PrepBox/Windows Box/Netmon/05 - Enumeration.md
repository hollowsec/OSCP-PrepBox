# Nmap
```bash
PORT    STATE SERVICE      VERSION                                                                                                                                                            
21/tcp  open  ftp          Microsoft ftpd                                                                                                                                                     
| ftp-syst:                                                                                                                                                                                   
|_  SYST: Windows_NT                                                                                                                                                                          
| ftp-anon: Anonymous FTP login allowed (FTP code 230)                                                                                                                                        
| 02-02-19  11:18PM                 1024 .rnd                                                                                                                                                 
| 02-25-19  09:15PM       <DIR>          inetpub                                                                                                                                              
| 07-16-16  08:18AM       <DIR>          PerfLogs                                                                                                                                             
| 02-25-19  09:56PM       <DIR>          Program Files                                                                                                                                        
| 02-02-19  11:28PM       <DIR>          Program Files (x86)                                                                                                                                  
| 02-03-19  07:08AM       <DIR>          Users                                                                                                                                                
|_02-25-19  10:49PM       <DIR>          Windows          
80/tcp  open  http         Indy httpd 18.1.37.13946 (Paessler PRTG bandwidth monitor)          
| http-title: Welcome | PRTG Network Monitor (NETMON)          
|_Requested resource was /index.htm
|_http-favicon: Unknown favicon MD5: 36B3EF286FA4BEFBB797A0966B456479                          
|_http-trane-info: Problem with XML parsing of /evox/about                                     
| http-methods:                            
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: PRTG/18.1.37.13946                                                       
135/tcp open  msrpc        Microsoft Windows RPC                                               
139/tcp open  netbios-ssn  Microsoft Windows netbios-ssn                                       
445/tcp open  microsoft-ds Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows       
                                               
Host script results:                                                                           
| smb2-time:                         
|   date: 2021-11-29T16:32:09
|_  start_date: 2021-11-29T16:28:43  
| smb-security-mode:   
|   authentication_level: user       
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)                                         
| smb2-security-mode:                  
|   3.1.1:                        
|_    Message signing enabled but not required
|_clock-skew: mean: 6m23s, deviation: 0s, median: 6m
```