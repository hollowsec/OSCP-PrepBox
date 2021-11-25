# Web Server on 80

## Fuzzing files/api

```bash
$ ffuf -u http://10.10.10.68/FUZZ -w /opt/SecLists/Discovery/Web-Content/raft-small-words.txt -c -o ffuf.main                                                                        
                   
... [snip] ...                                                                                                                                        
                             
uploads                 [Status: 301, Size: 312, Words: 20, Lines: 10]                                                                                                                                                                                                                                        
dev                     [Status: 301, Size: 308, Words: 20, Lines: 10]                                                                                                                        
```

## Found on /dev
![[Pasted image 20211105005828.png]]

* /dev/phpbash.php  take to  a semi-interactive web shell
![[Pasted image 20211105010236.png]]

