#### Bandit Level 32 → Level 33

After all this git stuff, it’s time for another escape. Good luck! (sh, man)

```shell
>> $0
$ ls -al
$ whoami
bandit33
$ cat /etc/bandit\_pass/bandit33
# tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```


#### Bandit Level 31 → Level 32
There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.
```shell
bandit30@bandit:~$ cd $(mktemp -d)
bandit30@bandit:/tmp/tmp.ClPZkvATLk$ git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
bandit30@bandit:/tmp/tmp.ClPZkvATLk$ cd repo
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ cat README
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ echo "May I come in?" >> key.txt
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ git add key.txt -f
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ git commit -m "May I come in?"
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ git remote add repo ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ git push repo master
# 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```

#### Bandit Level 30 → Level 31
There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.

```shell
bandit30@bandit:~$ cd $(mktemp -d)
bandit30@bandit:/tmp/tmp.ClPZkvATLk$ git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
bandit30@bandit:/tmp/tmp.ClPZkvATLk$ cd repo
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ cat README
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ git tag
bandit30@bandit:/tmp/tmp.ClPZkvATLk/repo$ git show secret
# fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```

#### Bandit Level 29 → Level 30
There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.

```shell
bandit29@bandit:~$ cd $(mktemp -d)
bandit29@bandit:/tmp/tmp.ClPZkvATLk$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
bandit29@bandit:/tmp/tmp.ClPZkvATLk$ cd repo
bandit29@bandit:/tmp/tmp.ClPZkvATLk/repo$ cat README
bandit29@bandit:/tmp/tmp.ClPZkvATLk/repo$ git log
bandit29@bandit:/tmp/tmp.ClPZkvATLk/repo$ git diff e65a928 6ac7796
#-- username: bandit29
#+- username: bandit30
# - password: <no passwords in production!>
bandit29@bandit:/tmp/tmp.ClPZkvATLk/repo$ git branch -a
#* master
#  remotes/origin/HEAD -> origin/master
#  remotes/origin/dev
#  remotes/origin/master
#  remotes/origin/sploits-dev
bandit29@bandit:/tmp/tmp.ClPZkvATLk/repo$ git switch dev
# qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```


#### Bandit Level 28 → Level 29
There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.

```shell
bandit28@bandit:~$ mktemp -d  # >> /tmp/tmp.ClPZkvATLk
bandit28@bandit:/tmp/tmp.ClPZkvATLk$ cd /tmp/tmp.ClPZkvATLk
bandit28@bandit:/tmp/tmp.ClPZkvATLk$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
bandit28@bandit:/tmp/tmp.ClPZkvATLk$ cd repo
bandit28@bandit:/tmp/tmp.ClPZkvATLk/repo$ cat README
bandit28@bandit:/tmp/tmp.ClPZkvATLk/repo$ git log
bandit28@bandit:/tmp/tmp.ClPZkvATLk/repo$ git diff 3621de89d8eac9d3b64302bfb2dc67e9a566decd
# 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```

#### Bandit Level 27 → Level 28
There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

```shell
bandit27@bandit:~$ mktemp -d  # >> /tmp/tmp.ClPZkvATLk
bandit27@bandit:/tmp/tmp.ClPZkvATLk$ cd /tmp/tmp.ClPZkvATLk
bandit27@bandit:/tmp/tmp.ClPZkvATLk$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
bandit27@bandit:/tmp/tmp.ClPZkvATLk$ cd repo
bandit27@bandit:/tmp/tmp.ClPZkvATLk/repo$ cat README
# Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```

#### Bandit Level 26 → Level 27
Good job getting a shell! Now hurry and grab the password for bandit27!

```shell
# login again to bangit26
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit\_pass/bandit27
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```

#### Bandit Level 25 → Level 26
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

```shell
bandit25@bandit:~$ ssh -i bandit26.sshkey bandit26@localhost -p 2220
# :e /etc/bandit\_pass/bandit26
# :set shell=/bin/bash
# :shell
# s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
```

#### Bandit Level 24 → Level 25
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time
```shell
bandit24@bandit:~$ python3
```
``` python
import socket
from time import sleep

host = '0.0.0.0'
port = 30002
bandit24_password = 'gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8'


def connect(s, pin):
    s.send(f"{bandit24_password} {pin}\n".encode())
    sleep(0.1)
    response = s.recv(1024).decode()
    return response


def brute_force_pincode(start=0, end=10_000):
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.connect((host, port))
        for i in range(start, end):
            pincode = f"{i:04d}"
            try:
                print(f"Trying pincode: {pincode}")
                response = connect(s, pincode)
                if "Wrong!" not in response:
                    print(f"Found the correct pincode: {pincode}")
                    print(f"Response: {response}")
                    return
            except Exception as e:
                print(f"Error with pincode {pincode}: {e}")
                continue


brute_force_pincode(840)

# Found the correct pincode: 9297
# Response: Correct!
# The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```


#### Bandit Level 23 → Level 24
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.
Commands you may need to solve this level
chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)
```shell
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
bandit23@bandit:~$ cd /var/spool/bandit24/foo
bandit23@bandit:~$ nano crack.sh

#!/bin/bash
log_file="/tmp/bandit24_files.txt"
echo "Logging started at $(date)" > "$log_file"
for item in /var/spool/bandit24/foo/*; do
    if [ -d "$item" ]; then
        echo "Directory: $item" >> "$log_file"
        ls -l "$item" >> "$log_file"
    elif [ -f "$item" ]; then
        echo "File: $item" >> "$log_file"
        cat "$item" >> "$log_file"
    fi
done

bandit23@bandit:~$ chmod -x /var/spool/bandit24/foo/crack.sh
bandit23@bandit:~$ chown bandit23:bandit23 /var/spool/bandit24/foo/crack.sh
bandit23@bandit:~$ /tmp/bandit24_files.txt
cat /etc/bandit_pass/bandit24 >> /tmp/tmp.pJeqHTifXQ/hubb

bandit23@bandit:~$ echo "cat /etc/bandit_pass/bandit24 > /tmp/bandit_log.txt" > /var/spool/bandit24/foo/crack.sh
bandit23@bandit:~$ chmod -x /var/spool/bandit24/foo/crack.sh
bandit23@bandit:~$ chown bandit23:bandit23 /var/spool/bandit24/foo/crack.sh
bandit23@bandit:~$ cat /tmp/bandit_log.txt
# gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```

#### Bandit Level 22 → Level 23
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

```shell
bandit22@bandit:~$ ls  /etc/cron.d/
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh
bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1 
# 8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
# 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```

#### Bandit Level 21 → Level 22
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

```shell
bandit21@bandit:~$ ls  /etc/cron.d/
bandit21@bandit:~$ cat  /etc/cron.d/cronjob_bandit22
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
# tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

#### Bandit Level 20 → Level 21
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

Commands you may need to solve this level
ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)

```shell
bandit20@bandit:~$ ls -l
bandit20@bandit:~$ (terminal_1) nc -l -p 8080
bandit20@bandit:~$ (terminal_2) ./suconnect 8080
bandit20@bandit:~$ (terminal_1) 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
# EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```

#### Bandit Level 19 → Level 20

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

**Helpful Reading Material**: 
setuid on Wikipedia

```shell
bandit19@bandit:~$ ls
bandit19@bandit:~$ bandit20-do
bandit19@bandit:~$ ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
# 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```


#### Bandit Level 18 → Level 19
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

**Commands you may need to solve this level:**
ssh, ls, cat

```shell
$ echo cat readme | ssh bandit18@bandit.labs.overthewire.org -p 2220 
# cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```


#### Bandit Level 17 → Level 18
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

**NOTE**: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

**Commands you may need to solve this level:**
cat, grep, ls, diff

```shell
bandit17@bandit:~$ ls
# passwords.new  passwords.old

bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< ktfgBvpMzWKR5ENj26IbLGSblgUG9CzB
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

# x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```

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

