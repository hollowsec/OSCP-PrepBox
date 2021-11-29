# Nmap
```bash
$ cat nmap/initial.nmap 
# Nmap 7.92 scan initiated Mon Nov 29 10:52:37 2021 as: nmap -sC -sV -oA nmap/initial 10.10.10.117
Nmap scan report for 10.10.10.117
Host is up (0.21s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 6.7p1 Debian 5+deb8u4 (protocol 2.0)
| ssh-hostkey: 
|   1024 6a:5d:f5:bd:cf:83:78:b6:75:31:9b:dc:79:c5:fd:ad (DSA)
|   2048 75:2e:66:bf:b9:3c:cc:f7:7e:84:8a:8b:f0:81:02:33 (RSA)
|   256 c8:a3:a2:5e:34:9a:c4:9b:90:53:f7:50:bf:ea:25:3b (ECDSA)
|_  256 8d:1b:43:c7:d0:1a:4c:05:cf:82:ed:c1:01:63:a2:0c (ED25519)
80/tcp  open  http    Apache httpd 2.4.10 ((Debian))
|_http-server-header: Apache/2.4.10 (Debian)
|_http-title: Site doesn't have a title (text/html).
111/tcp open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100024  1          40677/tcp   status
|   100024  1          46928/tcp6  status
|   100024  1          48086/udp6  status
|_  100024  1          48790/udp   status
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

```bash
sudo nmap -p- -oA nmap/allports 10.10.10.117

Nmap scan report for 10.10.10.117
Host is up (0.19s latency).
Scanned at 2021-11-29 10:55:28 -03 for 439s
Not shown: 65528 closed tcp ports (reset)
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
111/tcp   open  rpcbind
6697/tcp  open  ircs-u
8067/tcp  open  infi-async
40677/tcp open  unknown
65534/tcp open  unknown

```

```bash
$ sudo nmap -sC -sV -p 6697,8067,40677,65534 10.10.10.117 -Pn
[sudo] password for dix: 
Starting Nmap 7.92 ( https://nmap.org ) at 2021-11-29 11:07 -03
Nmap scan report for 10.10.10.117
Host is up (0.17s latency).

PORT      STATE SERVICE VERSION
6697/tcp  open  irc     UnrealIRCd
8067/tcp  open  irc     UnrealIRCd
40677/tcp open  status  1 (RPC #100024)
65534/tcp open  irc     UnrealIRCd
Service Info: Host: irked.htb
```

