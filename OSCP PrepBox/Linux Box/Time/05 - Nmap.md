# Nmap
Bionic Beaver - [4ubuntu0.1](https://launchpad.net/ubuntu/+source/openssh/1:7.6p1-4ubuntu0.1)
```sql
$ cat nmap/initial.nmap 
# Nmap 7.92 scan initiated Tue Dec 14 21:51:10 2021 as: nmap -sC -sV -oA nmap/initial 10.10.10.214
Nmap scan report for 10.10.10.214
Host is up (0.23s latency).
Scanned at 2021-12-14 21:51:12 -03 for 29s
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 0f:7d:97:82:5f:04:2b:e0:0a:56:32:5d:14:56:82:d4 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDqO75jA9cYksdPP+eBZBYzvJERbVfExL7kXpMJQpmpHoJdl9EG/wSsXgEH4BXsa56Rv2i32ClI7QvykILEpL6JyhHi3xS8vlNud8CQCYCYNCiBzpa84ucBbLpFaR331qH3n1PNrlBjvH0g4jmlQjlKMHRNSjxOS5XjO3JMYFhBkI3tZKXuo9dg/0wHwXXbGa5gFihkrTkGqinaPRACYC8FCgQ3UUpUzjTUUwSLMMMMAUJX+WkqPiD3++VCSmQmJn4rtOQK2PNzesJQFrHk5BLj6J2gfLUkgvVu2dMVCYAJ8Pom+sYRLq5dkBdaXugjpFXGWFXxYjh57h21HVtkdAVyObBu4iNlZQNYNPpYKuLbmTKdEv86FMfw/g1ZasV1q53gEc4vWyWVQSkarHXPyMYTY1nsFEIvkhGl8CsuwS0HioWaBRsF/+jQF+5Zty43VWJuu+PanAIOelmxAHrfNm//XrIW7RjqCLEDj0MpUeK4KUMx7WPuyE10zpESpuqhtAU=
|   256 24:ea:53:49:d8:cb:9b:fc:d6:c4:26:ef:dd:34:c1:1e (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBCY27npy127v6WaSs6QO9MlX1RCjlp8ceQ0UyP6SfI+Q7UZrmg0qLFANnuqkm8iNio+TLTTOIAv5itdE0ahgzgE=
|   256 fe:25:34:e4:3e:df:9f:ed:62:2a:a4:93:52:cc:cd:27 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFy9CB1oSRwsAZJb6AMVD7/T0qxBk2G7/hV2Db57c0Kj
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-favicon: Unknown favicon MD5: 7D4140C76BF7648531683BFA4F7F8C22
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Online JSON parser
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
```

