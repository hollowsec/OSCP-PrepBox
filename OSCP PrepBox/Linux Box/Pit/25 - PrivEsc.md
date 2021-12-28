# Getting Root
* Investigate the bin monitor (appear on snmpwalk)
* Content of monitor
```bash
#!/bin/bash

for script in /usr/local/monitoring/check*sh
do
    /bin/bash $script
done
monitor (END
```

* Altering content of monitor script for a ssh key
![[Pasted image 20211227233656.png]]

Run snmpwalk again to execute our payload (adding our ssh key on root authorized_keys)
```bash
$ snmpwalk -m +MY-MIB -v2c -c public 10.10.10.241 nsExtendObjects
```


![[Pasted image 20211228000451.png]]