# Nmap

```bash
PORT      STATE SERVICE      VERSION                                                           
80/tcp    open  http         Microsoft IIS httpd 10.0                                          
|_http-title: Ask Jeeves                                                                       
| http-methods:                      
|   Supported Methods: OPTIONS TRACE GET HEAD POST                                             
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
135/tcp   open  msrpc        Microsoft Windows RPC                                             
445/tcp   open  microsoft-ds Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)      
50000/tcp open  http         Jetty 9.4.z-SNAPSHOT                                              
| http-methods:                      
|_  Supported Methods: GET HEAD OPTIONS
|_http-title: Error 404 Not Found
|_http-server-header: Jetty(9.4.z-SNAPSHOT)                                                    
Service Info: Host: JEEVES; OS: Windows; CPE: cpe:/o:microsoft:windows
                                                                                               
Host script results:                
| smb2-time:                     
|   date: 2021-11-13T10:28:00              
|_  start_date: 2021-11-13T10:26:23        
| smb-security-mode:                      
|   authentication_level: user               
|   challenge_response: supported                                                              
|_  message_signing: disabled (dangerous, but default)                                         
| smb2-security-mode:             
|   3.1.1:                                                                                     
|_    Message signing enabled but not required
|_clock-skew: mean: 5h06m16s, deviation: 0s, median: 5h06m15s
```