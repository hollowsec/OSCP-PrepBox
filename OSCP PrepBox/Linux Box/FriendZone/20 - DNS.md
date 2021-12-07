# Transfer zone
### Dig (DNS)
```bash
$ dig axfr @10.10.10.123 friendzone.red > zonetransfer
$ dig axfr @10.10.10.123 friendzoneportal.red >> zonetransfer
```

```bash
$ cat zonetransfer 

; <<>> DiG 9.16.22-Debian <<>> axfr @10.10.10.123 friendzone.red
; (1 server found)
;; global options: +cmd
friendzone.red.         604800  IN      SOA     localhost. root.localhost. 2 604800 86400 2419200 604800
friendzone.red.         604800  IN      AAAA    ::1
friendzone.red.         604800  IN      NS      localhost.
friendzone.red.         604800  IN      A       127.0.0.1
administrator1.friendzone.red. 604800 IN A      127.0.0.1
hr.friendzone.red.      604800  IN      A       127.0.0.1
uploads.friendzone.red. 604800  IN      A       127.0.0.1
friendzone.red.         604800  IN      SOA     localhost. root.localhost. 2 604800 86400 2419200 604800
;; Query time: 176 msec
;; SERVER: 10.10.10.123#53(10.10.10.123)
;; WHEN: Tue Nov 30 10:24:15 -03 2021
;; XFR size: 8 records (messages 1, bytes 289)


; <<>> DiG 9.16.22-Debian <<>> axfr @10.10.10.123 friendzoneportal.red
; (1 server found)
;; global options: +cmd
friendzoneportal.red.   604800  IN      SOA     localhost. root.localhost. 2 604800 86400 2419200 604800
friendzoneportal.red.   604800  IN      AAAA    ::1
friendzoneportal.red.   604800  IN      NS      localhost.
friendzoneportal.red.   604800  IN      A       127.0.0.1
admin.friendzoneportal.red. 604800 IN   A       127.0.0.1
files.friendzoneportal.red. 604800 IN   A       127.0.0.1
imports.friendzoneportal.red. 604800 IN A       127.0.0.1
vpn.friendzoneportal.red. 604800 IN     A       127.0.0.1
friendzoneportal.red.   604800  IN      SOA     localhost. root.localhost. 2 604800 86400 2419200 604800
;; Query time: 172 msec
;; SERVER: 10.10.10.123#53(10.10.10.123)
;; WHEN: Tue Nov 30 10:24:51 -03 2021
;; XFR size: 9 records (messages 1, bytes 309)

``` 

### Treatment of zonetransfer file
```bash
$ cat zonetransfer | grep friendzone | grep IN | awk '{print $1}' | sed 's/\.$//g' | sort -u > hosts
```

```bash
$ cat hosts 
admin.friendzoneportal.red
administrator1.friendzone.red
files.friendzoneportal.red
friendzoneportal.red
friendzone.red
hr.friendzone.red
imports.friendzoneportal.red
uploads.friendzone.red
vpn.friendzoneportal.re
```

## Adding the hosts to the /etc/hosts

![[Pasted image 20211130103348.png]]

