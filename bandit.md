
#### Bandit Level 16 → Level 17
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
```shell
bandit16@bandit:~$ for port in {31000..32000}; do
    echo | openssl s_client -connect localhost:$port 2>/dev/null | grep "CONNECTED" && echo "Port $port supports SSL/TLS"
done

# CONNECTED(00000003)
# Port 31046 supports SSL/TLS
# CONNECTED(00000003)
# Port 31518 supports SSL/TLS
# CONNECTED(00000003)
# Port 31691 supports SSL/TLS
# CONNECTED(00000003)
# Port 31790 supports SSL/TLS
# CONNECTED(00000003)
# Port 31960 supports SSL/TLS

bandit16@bandit:~$ echo "kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx" | openssl s_client -connect localhost:31790 -quiet

-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

bandit16@bandit:~$ exit


$ touch bandit.perm
$ nano bandit.perm
$ chmod 600 bandit.perm
$ ssh -i bandit.perm bandit17@bandit.labs.overthewire.org -p 2220
```

#### Bandit Level 15 → Level 16
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.
```shell
# telnet does not support SSL/TLS encryption
# openssl s_client
#   This implements a generic SSL/TLS client which can establish a transparent connection to a remote server speaking SSL/TLS. It's
#   intended  for  testing  purposes  only  and  provides  only  rudimentary interface functionality but internally uses mostly all
#   functionality of the OpenSSL ssl library.
bandit15@bandit:~$ openssl s_client -help
# Parameters:
#  host:port   Where to connect; same as -connect option

bandit15@bandit:~$ openssl s_client 0.0.0.0:30000
# CONNECTED(00000003)
# SSL handshake has read 2103 bytes and written 373 bytes
# Verification error: self-signed certificate
# ....
# read R BLOCK
# 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
# Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

#### Bandit Level 14 → Level 15
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
```shell
bandit14@bandit:~$ telnet 0.0.0.0 30000
# Trying 0.0.0.0...
# Connected to 0.0.0.0.
# Escape character is '^]'.
# MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
# Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```


#### Bandit Level 13 → Level 14
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
```shell
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```



#### Bandit Level 12 → Level 13
```shell
Level 14 needs to connect via ssh
Copy ssh locally and grant it permission 
$ chmod 600 sshkey.private
```


#### Bandit Level 11 → Level 12
```shell
history 500
#   62  gzip -df data.txt.gz
#   88  gunzip -Sf /tmp/tmp.PjGfryW6EQ/data1.txt
#   92  mv data1.txt data.gz
#   94  gunzip data.gz
#  108  bzip2 -df data
#  112  cp data.out data-gz.gz
#  113  gunzip data-gz.gz
#  122  tar -xf data-gz
#  124  file data5.bin
#  127  tar -xvf data5.bin
#  129  tar -xvf data6.bin
#  130  tar -xvf data8.bin
#  135  cp data8.bin data8-gz.gz
#  136  gunzip data8-gz.gz
#  140  cat data8-gz
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

#### Level 11
```shell
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```


#### Level 10
```shell
bandit10@bandit:~$ cat data.txt | base64 -d
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```


#### Level 9
```shell
bandit9@bandit:~$ grep == -a data.txt
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```


#### Level 8
```shell
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```


###### Bandit Level 7 → Level 8
```shell
bandit7@bandit:~$ cat data.txt | grep millionth
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

#### or
```shell
bandit7@bandit:~$ grep millionth data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```


#### Bandit Level 6 → Level 7
```shell
bandit6@bandit:/$ find . -size 33c -user bandit7 -group bandit6 2>/dev/null | xargs cat
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```


#### Bandit Level 5 → Level 6
```bash
bandit5@bandit:~/inhere$ find ./inhere -size 1033c -print0 | xargs cat
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```



#### Bandit Level 4 → Level 5
```bash
bandit5@bandit:~/inhere$ cd inhere
bandit5@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```


#### Bandit Level 3 → Level 4
```bash
bandit3@bandit:~/inhere$ ls -a
inhere
bandit3@bandit:~/inhere$ cd inhere 
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat -A ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

#### Bandit Level 2 → Level 3
The password for the next level is stored in a file called - located in the home directory
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
bandit2@bandit:~$ ls
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```


#### Bandit Level 1 → Level 2
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat - 
>
bandit1@bandit:~$ cat ./-
# or bandit1@bandit:~$ cat -- -
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```


#### Bandit Level 0 → Level 1
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

