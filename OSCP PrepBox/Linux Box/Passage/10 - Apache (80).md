# Web Server on 80
web server has Fail2Ban

CMS = cutenews

![[Pasted image 20211214145029.png]]

```bash
$ searchsploit cutenews
```

![[Pasted image 20211214153406.png]]

![[Pasted image 20211214153433.png]]

http://10.10.10.206/CuteNews/cdata/users/lines
![[Pasted image 20211214153450.png]]


https://gchq.github.io/CyberChef/
![[Pasted image 20211214153531.png]]


![[Pasted image 20211214173149.png]]


```bash
$ cat output.txt | grep -oP [a-z0-9]{64} output.t
```

Hashes
```bash
7144a8b531c27a60b51d81ae16be3a81cef722e11b43a26fde0ca97f9e1485e1
4bdd0a0bb47fc9f66cbf1a8982fd2d344d2aec283d1afaebb4653ec3954dff88
e26f3e86d1f8108120723ebe690e5d3d61628f4130076ec6cb43f16f497273cd
f669a6f691f98ab0562356c0cd5d5e7dcdc20a07941c86adcfce9af3085fbeca
4db1f0bfd63be058d4ab04f18f65331ac11bb494b5792c480faf7fb0c40fa9cc
```
https://crackstation.net/
![[Pasted image 20211214175600.png]]

```bash
paul@passage.htb:e26f3e86d1f8108120723ebe690e5d3d61628f4130076ec6cb43f16f497273cd:sha256:atlanta1

egre55@test.com:4db1f0bfd63be058d4ab04f18f65331ac11bb494b5792c480faf7fb0c40fa9cc:sha256:egre55

```
