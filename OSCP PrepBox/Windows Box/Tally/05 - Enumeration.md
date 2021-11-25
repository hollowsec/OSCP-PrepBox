# Nmap

```bash
PORT     STATE SERVICE       VERSION                                                                                                                                                   [36/86]
21/tcp   open  ftp           Microsoft ftpd                                                                                                                                                   
| ftp-syst:                                                                                                                                                                                   
|_  SYST: Windows_NT                                                                           
80/tcp   open  http          Microsoft IIS httpd 10.0                                          
|_http-server-header: Microsoft-IIS/10.0
| http-methods:                           
|_  Supported Methods: HEAD POST OPTIONS  
| http-title: Home                                                                             
|_Requested resource was http://10.10.10.59/_layouts/15/start.aspx#/default.aspx               
|_http-favicon: Unknown favicon MD5: 50996DA127314E31E0B14D57B9847C9F                          
|_http-generator: Microsoft SharePoint        
81/tcp   open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)                           
|_http-server-header: Microsoft-HTTPAPI/2.0                                                    
|_http-title: Bad Request                                                                                                                                                                     
135/tcp  open  msrpc         Microsoft Windows RPC                                                                                                                                            
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn                                                                                                                                    
445/tcp  open  microsoft-ds  Microsoft Windows Server 2008 R2 - 2012 microsoft-ds                                                                                                             
808/tcp  open  ccproxy-http?                                                                                                                                                                  
1433/tcp open  ms-sql-s      Microsoft SQL Server 2016 13.00.1601.00; RTM                                                                                                                     
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback                                                                                                                                      
| Issuer: commonName=SSL_Self_Signed_Fallback                                                                                                                                                 
| Public Key type: rsa                                                                                                                                                                        
| Public Key bits: 2048                                                                        
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2021-11-16T03:12:58
| Not valid after:  2051-11-16T03:12:58                                                        
| MD5:   36a2 fbf1 359f beb1 0463 0006 7a28 fae0                                               
|_SHA-1: f241 e443 b824 f427 f441 5e3f e767 9142 1e14 b6e1                                     
|_ssl-date: 2021-11-16T04:03:02+00:00; +6m20s from scanner time.                               
| ms-sql-ntlm-info:    
|   Target_Name: TALLY               
|   NetBIOS_Domain_Name: TALLY              
|   NetBIOS_Computer_Name: TALLY                                                               
|   DNS_Domain_Name: TALLY                                                                     
|   DNS_Computer_Name: TALLY                                                                   
|_  Product_Version: 10.0.14393                                                                
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows 
```

