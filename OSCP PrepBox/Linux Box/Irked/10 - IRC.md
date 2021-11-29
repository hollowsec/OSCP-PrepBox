# IRC(8067)
https://datatracker.ietf.org/doc/html/rfc1459#section-4.1
```bash
$ nc -v 10.10.10.117 8067
10.10.10.117: inverse host lookup failed: Unknown host
(UNKNOWN) [10.10.10.117] 8067 (?) open
:irked.htb NOTICE AUTH :*** Looking up your hostname...
PASS eris
NICK eris
:irked.htb NOTICE AUTH :*** Couldn't resolve your hostname; using your IP address instead
USER eris HostJojo ServerMojo :eris
:irked.htb 001 eris :Welcome to the ROXnet IRC Network eris!eris@10.10.14.21
:irked.htb 002 eris :Your host is irked.htb, running version Unreal3.2.8.1
:irked.htb 003 eris :This server was created Mon May 14 2018 at 13:12:50 EDT
:irked.htb 004 eris irked.htb Unreal3.2.8.1 iowghraAsORTVSxNCWqBzvdHtGp lvhopsmntikrRcaqOALQbSeIKVfMCuzNTGj
:irked.htb 005 eris UHNAMES NAMESX SAFELIST HCN MAXCHANNELS=10 CHANLIMIT=#:10 MAXLIST=b:60,e:60,I:60 NICKLEN=30 CHANNELLEN=32 TOPICLEN=307 KICKLEN=307 AWAYLEN=307 MAXTARGETS=20 :are supported by this server
:irked.htb 005 eris WALLCHOPS WATCH=128 WATCHOPTS=A SILENCE=15 MODES=12 CHANTYPES=# PREFIX=(qaohv)~&@%+ CHANMODES=beI,kfL,lj,psmntirRcOAQKVCuzNSMTG NETWORK=ROXnet CASEMAPPING=ascii EXTBAN=~,cqnr ELIST=MNUCT STATUSMSG=~&@%+ :are supported by this server
:irked.htb 005 eris EXCEPTS INVEX CMDS=KNOCK,MAP,DCCALLOW,USERIP :are supported by this server
:irked.htb 251 eris :There are 1 users and 0 invisible on 1 servers
:irked.htb 255 eris :I have 1 clients and 0 servers
:irked.htb 265 eris :Current Local Users: 1  Max: 1
:irked.htb 266 eris :Current Global Users: 1  Max: 1
:irked.htb 422 eris :MOTD File is missing
:eris MODE eris :+iwx

```
/* Unreal 3.2.8.1 has vulnerability
https://blog.stalkr.net/2010/06/unrealircd-3281-backdoored.html
![[Pasted image 20211129112621.png]]