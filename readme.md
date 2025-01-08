## Bandit

This repo contains the solution to Bandit challenges. Check [original link to competitions](https://overthewire.org/wargames/bandit/)

Find solutions at [Bandit.dm](./bandit.md)

### Networking Tools

- `nmap` - Network exploration tool and security / port scanner. determine what hosts are available on the network
```shell
nmap -p 31000-32000 localhost
nmap -A -T4 scanme.nmap.org

Nmap scan report for scanme.nmap.org (74.207.244.221)
Host is up (0.029s latency).
rDNS record for 74.207.244.221: li86-221.members.linode.com
Not shown: 995 closed ports
PORT     STATE    SERVICE     VERSION
22/tcp   open     ssh         OpenSSH 5.3p1 Debian 3ubuntu7 (protocol 2.0)
| ssh-hostkey: 1024 8d:60:f1:7c:ca:b7:3d:0a:d6:67:54:9d:69:d9:b9:dd (DSA)
|_2048 79:f8:09:ac:d4:e2:32:42:10:49:d3:bd:20:82:85:ec (RSA)
80/tcp   open     http        Apache httpd 2.2.14 ((Ubuntu))
|_http-title: Go ahead and ScanMe!
646/tcp  filtered ldp
1720/tcp filtered H.323/Q.931
9929/tcp open     nping-echo  Nping echo
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6.39
OS details: Linux 2.6.39
Network Distance: 11 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:kernel
```
- `netstat` - Basic networking tool for connecting, transferring files, and scanning ports. Displays open network sockets, routing tables, and a number of network interface (network interface controller or software-defined network interface) and network protocol statistics.
```shell
netstat -tuln
ss -tuln | grep 31
# -t show TCP
# -u show UDP
# -l Display only listening sockets (these are omitted by default).
# -n Do not try to resolve service names
```

- `socat` (short for "SOcket CAT") - more versatile and powerful tool compared to ncat (or netcat). Establish two bidirectional byte streams and transfers data between them. This tool used for networking and data transfer, capable of creating a wide range of communication channels
- `ncat` - (netcat) for connecting to non-SSL servers. more advanced version of nc, ncat is part of the Nmap project and adds features and improvements over the traditional netcat. Supports SSL/TLS for encrypted connections, Allows for various proxy types (HTTP, SOCKS, etc.), Listening with SSL
For Non-SSL Ports:
``` shell
nc localhost <port>
```

For SSL Ports:
```shell
openssl s_client -connect localhost:<port>
```
- `nc` - reading from and writing to network connections using TCP or UDP. Port Scanning, File Transfers, Creating Simple Servers
```shell
# Create a server
nc -l -p 8080  
# -l - listen TCP
# -p - on port 8080
```

```bash
# Create a TCP server that echoes back received data:
socat TCP-LISTEN:1234,fork STDOUT
## Connect to created TCP server
telnet localhost 1234
openssl s_client 0.0.0.0:1234


# Forward TCP traffic from one port to another:
socat TCP-LISTEN:8080,fork TCP:localhost:80

# Create Port Proxy: Transfer a file over a TCP connection:

# receiver:
socat -v TCP-LISTEN:1234,fork FILE:received_file.txt

# sender:
socat FILE:some_file.txt TCP:localhost:1234
```
- `telnet` - used to communicate with remote devices over a TCP/IP network. Telnet does not support SSL/TLS encryption. It allows users to connect to remote servers and devices, primarily for remote management or accessing network services. Better (secure) alternative would be `ssh`.
```bash
# Connecting to a Host, or check if open
telnet localhost 22
```
- `openssl` - provides a variety of cryptographic operations and functionalities. SSL/TLS Management, Certificate Creation and Management, Key Generation, Data Encryption/Decryption and many more.
```shell
# telnet does not support SSL/TLS encryption
# openssl s_client
#   This implements a generic SSL/TLS client which can establish a transparent connection to a remote server speaking SSL/TLS. It's
#   intended  for  testing  purposes  only  and  provides  only  rudimentary interface functionality but internally uses mostly all
#   functionality of the OpenSSL ssl library.
openssl s_client -help
# Parameters:
#  host:port   Where to connect; same as -connect option

openssl s_client 0.0.0.0:30000
# CONNECTED(00000003)
# SSL handshake has read 2103 bytes and written 373 bytes
# Verification error: self-signed certificate
# ....
# read R BLOCK
# 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
# Correct!
```

#### Cron configuration
```shell
$ lcat /etc/cron.d/<file_name>

@reboot bandit23 /usr/bin/cronjob_bandit23.sh &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null

## Line 1
# @reboot: This means the job will execute once at system startup or reboot.
# bandit23: Specifies the user bandit23 under whose context the job will run.
# /usr/bin/cronjob_bandit23.sh: The script to be executed (cronjob_bandit23.sh) located in /usr/bin/.
# &> /dev/null: Redirects both standard output (stdout) and standard error (stderr) to /dev/null, effectively discarding any output or error messages.


## Line 2:
# * * * * *: Represents the cron timing fields, meaning:
# - Minute: * (every minute)
# - Hour: * (every hour)
# - Day of the month: * (every day)
# - Month: * (every month)
# - Day of the week: * (every day of the week)
# - Together, this means the job will run every minute.
```
