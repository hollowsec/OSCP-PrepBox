# Nmap
```bash
$ cat nmap/initial.nmap 
# Nmap 7.92 scan initiated Tue Dec 14 14:10:34 2021 as: nmap -sC -sV -oA nmap/initial 10.10.10.206
Nmap scan report for 10.10.10.206
Host is up (0.25s latency).
Scanned at 2021-12-14 14:10:35 -03 for 17s
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 17:eb:9e:23:ea:23:b6:b1:bc:c6:4f:db:98:d3:d4:a1 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDVnCUEEK8NK4naCBGc9im6v6c67d5w/z/i72QIXW9JPJ6bv/rdc45FOdiOSovmWW6onhKbdUje+8NKX1LvHIiotFhc66Jih+AW8aeK6pIsywDxtoUwBcKcaPkVFIiFUZ3UWOsWMi+qYTFGg2DEi3OHHWSMSPzVTh+YIsCzkRCHwcecTBNipHK645LwdaBLESJBUieIwuIh8icoESGaNcirD/DkJjjQ3xKSc4nbMnD7D6C1tIgF9TGZadvQNqMgSmJJRFk/hVeA/PReo4Z+WrWTvPuFiTFr8RW+yY/nHWrG6LfldCUwpz0jj/kDFGUDYHLBEN7nsFZx4boP8+p52D8F
|   256 71:64:51:50:c3:7f:18:47:03:98:3e:5e:b8:10:19:fc (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBCdB2wKcMmurynbHuHifOk3OGwNcZ1/7kTJM67u+Cm/6np9tRhyFrjnhcsmydEtLwGiiY5+tUjr2qeTLsrgvzsY=
|   256 fd:56:2a:f8:d0:60:a7:f1:a0:a1:47:a4:38:d6:a8:a1 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGRIhMr/zUartoStYphvYD6kVzr7TDo+gIQfS2WwhSBd
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Passage News
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
```
