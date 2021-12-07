## Using Aquatone to take screenshots of all pages for quick examination

```bash
$ cat hosts | aquatone                                                                                                                                                       [11/138]
aquatone v1.7.0 started at 2021-11-30T10:51:09-03:00                                           
                                                                                               
Targets    : 9                                                                                 
Threads    : 4                                                                                 
Ports      : 80, 443, 8000, 8080, 8443
Output dir : .                                                                                 
                                               
https://imports.friendzoneportal.red: 404 Not Found                                            
https://hr.friendzone.red: 404 Not Found       
https://admin.friendzoneportal.red: 200 OK     
https://friendzone.red: 200 OK                                                                 
https://administrator1.friendzone.red: 200 OK
https://files.friendzoneportal.red: 404 Not Found
https://friendzoneportal.red: 200 OK
https://vpn.friendzoneportal.red: 404 Not Found
https://uploads.friendzone.red: 200 OK
https://admin.friendzoneportal.red: screenshot successful
https://imports.friendzoneportal.red: screenshot successful
https://hr.friendzone.red: screenshot successful
https://files.friendzoneportal.red: screenshot successful
https://friendzone.red: screenshot successful
https://administrator1.friendzone.red: screenshot successful
https://vpn.friendzoneportal.red: screenshot successful
https://uploads.friendzone.red: screenshot successful
https://friendzoneportal.red: screenshot successful
Calculating page structures... done
Clustering similar pages... done
Generating HTML report... done

Writing session file...Time:
 - Started at  : 2021-11-30T10:51:09-03:00
 - Finished at : 2021-11-30T10:51:19-03:00
 - Duration    : 10s

Requests:
 - Successful : 9
 - Failed     : 0

 - 2xx : 5
 - 3xx : 0
 - 4xx : 4
 - 5xx : 0

Screenshots:
 - Successful : 9
 - Failed     : 0
```


 View the report
```bash
$ firefox aquatone_report.htm
```
![[Pasted image 20211130105512.png]]


### SubDomains
https://administrator1.friendzone.red/

https://admin.friendzoneportal.red

 https://uploads.friendzone.red
 
 