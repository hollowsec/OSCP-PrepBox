# Exploring FTP
Creds:
Username: developer
Original-Password: m^AsY7vTKVT+dV1{WOU%@NaHkUAId3]C

Download ftp directories to local machine

```bash
$ wget --user developer --password 'm^AsY7vTKVT+dV1{WOU%@NaHkUAId3]C' -r ftp://10.10.10.197
```
nothing interesting in the files
only found a subdomain dev.sneakycorp.htb to add on /etc/hosts

Can try upload file on ftp to get a reverse shell