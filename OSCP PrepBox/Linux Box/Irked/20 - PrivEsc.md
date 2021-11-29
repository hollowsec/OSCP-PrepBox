# Getting Root

![[Pasted image 20211129113640.png]]

```
Super elite steg backup pw
UPupDOWNdownLRlrBAbaSSss
```

donwload the unique image on the machine which is on web server
```bash
curl http://10.10.10.117/irked.jpg -o irked.jpg
```

```bash
$ cat pass.txt 
Kab6h+m+bbp2J:HG
```
![[Pasted image 20211129114300.png]]

### Trying to ssh with this pass on user djmardov

![[Pasted image 20211129114527.png]]

Suspect binary
![[Pasted image 20211129124100.png]]

```bash
$ ltrace ./viewuser
```

![[Pasted image 20211129125605.png]]

![[Pasted image 20211129125820.png]]