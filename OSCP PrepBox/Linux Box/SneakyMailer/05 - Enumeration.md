# Nmap
```bash
# Nmap 7.92 scan initiated Mon Dec 13 17:39:03 2021 as: nmap -sC -sV -oA nmap/initial 10.10.10.197
Nmap scan report for 10.10.10.197
Host is up (0.26s latency).
Scanned at 2021-12-13 17:39:04 -03 for 81s
Not shown: 993 closed tcp ports (reset)
PORT     STATE SERVICE  VERSION
21/tcp   open  ftp      vsftpd 3.0.3
22/tcp   open  ssh      OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   2048 57:c9:00:35:36:56:e6:6f:f6:de:86:40:b2:ee:3e:fd (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCy6l2NxLZItm85sZuNKU/OzDEhlvYMmmrKpTD0+uxdQyySppZN3Lo6xOM2dC6pqG5DQjz+GPJl1/kbdla6qJXDZ1D5lnnCaImTqU++a1WceLck3/6/04B5RlTYUoLQFwRuy84CX8NDvs0mIyR7bpbd8W03+EAwTabOxXfukQG1MbgCY5V8QmLRdi/ZtsIqVxVZWOYI5rvuAQ+YM9D/Oa6mwAO5l2V3/h/A5nHDx2Vkl1++kfDqFNop2D2vssInvdwLKZ0M5RvXLQPlsqRLfqtcTBBLxYY6ZVcLHkvEA+gekHGcPRw0MV5U9vsx18+6O8wm9ZNI/a1Y4TyXIHMcbHi9
|   256 d8:21:23:28:1d:b8:30:46:e2:67:2d:59:65:f0:0a:05 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBOHL62JJEI1N8SHtcSypj9IjyD3dm6CA5iyog1Rmi4P5N6VtA/5RxBxegMYv7bTFymmFm02+w9zXdKMUcSs5TbE=
|   256 5e:4f:23:4e:d4:90:8e:e9:5e:89:74:b3:19:0c:fc:1a (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILZ/TeP6ZPj9zbHyFVfwZg48EElGqKCENQgPw+QCoC7x
25/tcp   open  smtp     Postfix smtpd
|_smtp-commands: debian, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN, SMTPUTF8, CHUNKING
80/tcp   open  http     nginx 1.14.2
|_http-title: Did not follow redirect to http://sneakycorp.htb
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: nginx/1.14.2
143/tcp  open  imap     Courier Imapd (released 2018)
|_ssl-date: TLS randomness does not represent time
|_imap-capabilities: IMAP4rev1 ACL2=UNION THREAD=ORDEREDSUBJECT THREAD=REFERENCES ACL completed CHILDREN IDLE ENABLE CAPABILITY SORT NAMESPACE OK UTF8=ACCEPTA0001 QUOTA STARTTLS UIDPLUS
| ssl-cert: Subject: commonName=localhost/organizationName=Courier Mail Server/stateOrProvinceName=NY/countryName=US/organizationalUnitName=Automatically-generated IMAP SSL key/localityName=New York
| Subject Alternative Name: email:postmaster@example.com
| Issuer: commonName=localhost/organizationName=Courier Mail Server/stateOrProvinceName=NY/countryName=US/organizationalUnitName=Automatically-generated IMAP SSL key/localityName=New York
| Public Key type: rsa
| Public Key bits: 3072
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-05-14T17:14:21
| Not valid after:  2021-05-14T17:14:21
| MD5:   3faf 4166 f274 83c5 8161 03ed f9c2 0308
| SHA-1: f79f 040b 2cd7 afe0 31fa 08c3 b30a 5ff5 7b63 566c
| -----BEGIN CERTIFICATE-----
| MIIE6zCCA1OgAwIBAgIBATANBgkqhkiG9w0BAQsFADCBjjESMBAGA1UEAxMJbG9j
| YWxob3N0MS0wKwYDVQQLEyRBdXRvbWF0aWNhbGx5LWdlbmVyYXRlZCBJTUFQIFNT
| TCBrZXkxHDAaBgNVBAoTE0NvdXJpZXIgTWFpbCBTZXJ2ZXIxETAPBgNVBAcTCE5l
| dyBZb3JrMQswCQYDVQQIEwJOWTELMAkGA1UEBhMCVVMwHhcNMjAwNTE0MTcxNDIx
| WhcNMjEwNTE0MTcxNDIxWjCBjjESMBAGA1UEAxMJbG9jYWxob3N0MS0wKwYDVQQL
| EyRBdXRvbWF0aWNhbGx5LWdlbmVyYXRlZCBJTUFQIFNTTCBrZXkxHDAaBgNVBAoT
| E0NvdXJpZXIgTWFpbCBTZXJ2ZXIxETAPBgNVBAcTCE5ldyBZb3JrMQswCQYDVQQI
| EwJOWTELMAkGA1UEBhMCVVMwggGiMA0GCSqGSIb3DQEBAQUAA4IBjwAwggGKAoIB
| gQDCzBP4iuxxLmXPkmi5jABQrywLJK0meyW49umfYhqayBH7qtuIjyAmznnyDIR0
| 543qHgWAfSvGHLFDB9B1wnkvAU3aprjURn1956X/4jEi9xmhRwvum5T+vp3TT96d
| JgW9SSLiPFQty5eVrKuQvg1bZg/Vjp7CUUQ0+7PmdylMOipohls5RDEppCDGFmiS
| HN0ZayXpjd/kwqZ/O9uTJGHOzagY+ruTYAx3tanO4oDwdrz9FPr3S2KNPTjjtzqf
| CPdcsi+6JTQJI03eMEftBKo3HZTp7Hx6FObZcvcNskTLqtsYZYuzHS7KQwiuTAJ5
| d/ZKowCeJDaVlS35tQleisu+pJCkwcStpM1BJ51UQRZ5IpvItTfnrChEa1uyTlAy
| ZIOQK2/+34K2ZrldYWyfKlYHxieGZgzQXLo/vyW/1gqzXy7KHx+Uuf4CAzzOP1p3
| 8QNmvsqkJrQMuH3XPXLswr9A1gPe7KTLEGNRJSxcGF1Q25m4e04HhZzK76KlBfVt
| IJ0CAwEAAaNSMFAwDAYDVR0TAQH/BAIwADAhBgNVHREEGjAYgRZwb3N0bWFzdGVy
| QGV4YW1wbGUuY29tMB0GA1UdDgQWBBTylxdM/AHlToKxNvmnPdXJCjjbnDANBgkq
| hkiG9w0BAQsFAAOCAYEAAo7NqfYlXSEC8q3JXvI5EeVpkgBDOwnjxuC/P5ziEU0c
| PRx6L3w+MxuYJdndC0hT9FexXzSgtps9Xm+TE81LgNvuipZ9bulF5pMmmO579U2Y
| suJJpORD4P+65ezkfWDbPbdKyHMeRvVCkZCH74z2rCu+OeQTGb6GLfaaB7v9dThR
| rfvHwM50hxNb4Zb4of7Eyw2OJGeeohoG4mFT4v7cu1WwimsDF/A7OCVOmvvFWeRA
| EjdEReekDJsBFpHa8uRjxZ+4Ch9YvbFlYtYi6VyXV1AFR1Mb91w+iIitc6ROzjJ2
| pVO69ePygQcjBRUTDX5reuBzaF5p9/6Ta9HP8NDI9+gdw6VGVTmYRJUbj7OeKSUq
| FWUmtZYC288ErDAZ7z+6VqJtZsPXIItZ8J6UZE3zBclGMcQ7peL9wEvJQ8oSaHHM
| AmgHIoMwKXSNEkHbBD24cf9KwVhcyJ4QCrSJBMAys98X6TzCwQI4Hy7XyifU3x/L
| XUFD0JSVQp4Rmcg5Uzuk
|_-----END CERTIFICATE-----
993/tcp  open  ssl/imap Courier Imapd (released 2018)
| ssl-cert: Subject: commonName=localhost/organizationName=Courier Mail Server/stateOrProvinceName=NY/countryName=US/organizationalUnitName=Automatically-generated IMAP SSL key/localityName=New York
| Subject Alternative Name: email:postmaster@example.com
| Issuer: commonName=localhost/organizationName=Courier Mail Server/stateOrProvinceName=NY/countryName=US/organizationalUnitName=Automatically-generated IMAP SSL key/localityName=New York
| Public Key type: rsa
| Public Key bits: 3072
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2020-05-14T17:14:21
| Not valid after:  2021-05-14T17:14:21
| MD5:   3faf 4166 f274 83c5 8161 03ed f9c2 0308
| SHA-1: f79f 040b 2cd7 afe0 31fa 08c3 b30a 5ff5 7b63 566c
| -----BEGIN CERTIFICATE-----
| MIIE6zCCA1OgAwIBAgIBATANBgkqhkiG9w0BAQsFADCBjjESMBAGA1UEAxMJbG9j
| YWxob3N0MS0wKwYDVQQLEyRBdXRvbWF0aWNhbGx5LWdlbmVyYXRlZCBJTUFQIFNT
| TCBrZXkxHDAaBgNVBAoTE0NvdXJpZXIgTWFpbCBTZXJ2ZXIxETAPBgNVBAcTCE5l
| dyBZb3JrMQswCQYDVQQIEwJOWTELMAkGA1UEBhMCVVMwHhcNMjAwNTE0MTcxNDIx
| WhcNMjEwNTE0MTcxNDIxWjCBjjESMBAGA1UEAxMJbG9jYWxob3N0MS0wKwYDVQQL
| EyRBdXRvbWF0aWNhbGx5LWdlbmVyYXRlZCBJTUFQIFNTTCBrZXkxHDAaBgNVBAoT
| E0NvdXJpZXIgTWFpbCBTZXJ2ZXIxETAPBgNVBAcTCE5ldyBZb3JrMQswCQYDVQQI
| EwJOWTELMAkGA1UEBhMCVVMwggGiMA0GCSqGSIb3DQEBAQUAA4IBjwAwggGKAoIB
| gQDCzBP4iuxxLmXPkmi5jABQrywLJK0meyW49umfYhqayBH7qtuIjyAmznnyDIR0
| 543qHgWAfSvGHLFDB9B1wnkvAU3aprjURn1956X/4jEi9xmhRwvum5T+vp3TT96d
| JgW9SSLiPFQty5eVrKuQvg1bZg/Vjp7CUUQ0+7PmdylMOipohls5RDEppCDGFmiS
| HN0ZayXpjd/kwqZ/O9uTJGHOzagY+ruTYAx3tanO4oDwdrz9FPr3S2KNPTjjtzqf
| CPdcsi+6JTQJI03eMEftBKo3HZTp7Hx6FObZcvcNskTLqtsYZYuzHS7KQwiuTAJ5
| d/ZKowCeJDaVlS35tQleisu+pJCkwcStpM1BJ51UQRZ5IpvItTfnrChEa1uyTlAy
| ZIOQK2/+34K2ZrldYWyfKlYHxieGZgzQXLo/vyW/1gqzXy7KHx+Uuf4CAzzOP1p3
| 8QNmvsqkJrQMuH3XPXLswr9A1gPe7KTLEGNRJSxcGF1Q25m4e04HhZzK76KlBfVt
| IJ0CAwEAAaNSMFAwDAYDVR0TAQH/BAIwADAhBgNVHREEGjAYgRZwb3N0bWFzdGVy
| QGV4YW1wbGUuY29tMB0GA1UdDgQWBBTylxdM/AHlToKxNvmnPdXJCjjbnDANBgkq
| hkiG9w0BAQsFAAOCAYEAAo7NqfYlXSEC8q3JXvI5EeVpkgBDOwnjxuC/P5ziEU0c
| PRx6L3w+MxuYJdndC0hT9FexXzSgtps9Xm+TE81LgNvuipZ9bulF5pMmmO579U2Y
| suJJpORD4P+65ezkfWDbPbdKyHMeRvVCkZCH74z2rCu+OeQTGb6GLfaaB7v9dThR
| rfvHwM50hxNb4Zb4of7Eyw2OJGeeohoG4mFT4v7cu1WwimsDF/A7OCVOmvvFWeRA
| EjdEReekDJsBFpHa8uRjxZ+4Ch9YvbFlYtYi6VyXV1AFR1Mb91w+iIitc6ROzjJ2
| pVO69ePygQcjBRUTDX5reuBzaF5p9/6Ta9HP8NDI9+gdw6VGVTmYRJUbj7OeKSUq
| FWUmtZYC288ErDAZ7z+6VqJtZsPXIItZ8J6UZE3zBclGMcQ7peL9wEvJQ8oSaHHM
| AmgHIoMwKXSNEkHbBD24cf9KwVhcyJ4QCrSJBMAys98X6TzCwQI4Hy7XyifU3x/L
| XUFD0JSVQp4Rmcg5Uzuk
|_-----END CERTIFICATE-----
|_ssl-date: TLS randomness does not represent time
8080/tcp open  http     nginx 1.14.2
|_http-title: Welcome to nginx!
|_http-open-proxy: Proxy might be redirecting requests
| http-methods: 
|_  Supported Methods: GET HEAD
|_http-server-header: nginx/1.14.2
Service Info: Host:  debian; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Mon Dec 13 17:40:25 2021 -- 1 IP address (1 host up) scanned in 82.03 seconds

```