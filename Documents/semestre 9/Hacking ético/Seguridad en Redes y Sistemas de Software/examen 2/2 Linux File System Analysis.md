## Objetivo
Perform real-time file system analysis on a Linux system to identify an attacker's artefacts.
## Solución
investigator@ip-10-10-143-60:~$ export PATH=/mnt/usb/bin:/mnt/usb/
sbin
investigator@ip-10-10-143-60:~$ export LD_LIBRARY_PATH=/mnt/usb/li
b:/mnt/usb/lib64
investigator@ip-10-10-143-60:~$ check-env
THM{5514ec4f1ce82f63867806d3cd95dbd8}
find: ‘/var/log/private’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/cron/atjobs’: Permission denied
find: ‘/var/spool/cron/atspool’: Permission denied
find: ‘/var/spool/postfix/maildrop’: Permission denieds. Check your Internet connection or proxy settings
find: ‘/var/spool/postfix/private’: Permission denied
find: ‘/var/spool/postfix/flush’: Permission denied
find: ‘/var/spool/postfix/defer’: Permission denied
find: ‘/var/spool/postfix/bounce’: Permission denied
find: ‘/var/spool/postfix/corrupt’: Permission denied
find: ‘/var/spool/postfix/deferred’: Permission denied
find: ‘/var/spool/postfix/saved’: Permission denied
find: ‘/var/spool/postfix/public’: Permission denied
find: ‘/var/spool/postfix/active’: Permission denied
find: ‘/var/spool/postfix/incoming’: Permission denied
investigator@ip-10-10-143-60:~$ cat /var/tmp/findme.txt
THM{0b1313afd2136ca0faafb2daa2b430f3}
investigator@ip-10-10-143-60:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/u
sr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/syste
md:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd:/usr/sb
in/nologin
systemd-timesync:x:102:104:systemd Time Synchronization,,,:/run/sy
stemd:/usr/sbin/nologin
messagebus:x:103:106::/nonexistent:/usr/sbin/nologin
syslog:x:104:110::/home/syslog:/usr/sbin/nologin
_apt:x:105:65534::/nonexisten
:/nonexistent:/usr/sbin/nologin
tss:x:106:111:TPM software stack,,,:/var/lib/tpm:/bin/false
uuidd:x:107:112::/run/uuidd:/usr/sbin/nologin
tcpdump:x:108:113::/nonexistent:/usr/sbin/nologin
sshd:x:109:65534::/run/sshd:/usr/sbin/nologin
landscape:x:110:115::/var/lib/landscape:/usr/sbin/nologin
pollinate:x:111:1::/var/cache/pollinate:/bin/false
ec2-instance-connect:x:112:65534::/nonexistent:/usr/sbin/nologin
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false
bob:x:1001:1001::/home/bob:/bin/bash
jane:x:1002:1002:Jane Walkers,103,9399499494,2029384958:/home/jane
:/bin/bash
investigator:x:1003:1003:Investigator,1,1,1,1:/home/investigator:/
bin/bash
postfix:x:113:120::/var/spool/postfix:/usr/sbin/nologin
b4ckd00r3d:x:0:1004::/home/b4ckd00r3d:/bin/sh
investigator@ip-10-10-143-60:~$ cat /etc/group | grep 46
plugdev:x:46:ubuntu,investigator
investigator@ip-10-10-143-60:~$ sudo cat /etc/sudoers | grep jane
[sudo] password for investigator: 
jane ALL=(ALL) /usr/bin/pstree
investigator@ip-10-10-143-60:~$ ^C
investigator@ip-10-10-143-60:~$ 
-rw-r--r-- 1 investigator investigator
investigator@ip-10-10-143-60:~$ cd /home/jane/
investigator@ip-10-10-143-60:/home/jane$ sudo cat .bash_history 
whoami
groups
cd ~
ls -al
find / -perm -u=s -type f 2>/dev/null
/usr/bin/python3.8 -c 'import os; os.execl("/bin/sh", "sh", "-p", 
"-c", "cp /bin/bash /var/tmp/bash && chown root:root /var/tmp/bash
 && chmod +s /var/tmp/bash")'
ls -al /var/tmp
exit
useradd -o -u 0 b4ckd00r3d
exit
THM{f38279ab9c6af1215815e5f7bbad891b}
investigator@ip-10-10-143-60:/home/jane$ cd /home/bob/
investigator@ip-10-10-143-60:/home/bob$ ^C
investigator@ip-10-10-143-60:/home/bob$ ls -la
total 36
drwxr-xr-x 4 bob  bob  4096 Feb 12  2024 .
drwxr-xr-x 6 root root 4096 Feb 12  2024 ..
-rw-r--r-- 1 bob  bob   220 Feb 12  2024 .bash_logout
-rw-r--r-- 1 bob  bob  3771 Feb 12  2024 .bashrc
drwx------ 2 bob  bob  4096 Feb 12  2024 .cache
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden1
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden10
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden11
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden12
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden13
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden14
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden15
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden16
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden17
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden18
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden19
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden2
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden20
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden21
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden22
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden23
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden24
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden25
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden26
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden27
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden28
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden29
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden3
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden30
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden31
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden32
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden33
-rw-rw-r-- 1 bob  bob    38 Feb 12  2024 .hidden34
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden35
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden36
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden37
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden38
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden39
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden4
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden40
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden41
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden42
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden43
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden44
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden45
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden46
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden47
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden48
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden49
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden5
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden50
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden6
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden7
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden8
-rw-rw-r-- 1 bob  bob     0 Feb 12  2024 .hidden9
drwxrwxr-x 3 bob  bob  4096 Feb 12  2024 .local
-rw-r--r-- 1 bob  bob   807 Feb 12  2024 .profi
-rw-rw-r-- 1 bob  bob    66 Feb 12  2024 .selected_editor
investigator@ip-10-10-143-60:/home/bob$ cat .hidden34
THM{6ed90e00e4fb7945bead8cd59e9fcd7f}
investigator@ip-10-10-143-60:/home/bob$ cd /home/jane/
investigator@ip-10-10-143-60:/home/jane$ cd .ssh/
investigator@ip-10-10-143-60:/home/jane/.ssh$ ls -la
total 20
drwxr-xr-x 2 jane jane 4096 Feb 12  2024 .
drwxr-xr-x 4 jane jane 4096 Feb 13  2024 ..
-rw-rw-rw- 1 jane jane 1136 Feb 13  2024 authorized_keys
-rw------- 1 jane jane 3389 Feb 12  2024 id_rsa
-rw-r--r-- 1 jane jane  746 Feb 12  2024 id_rsa.pub
investigator@ip-10-10-143-60:/home/jane/.ssh$ stat authorized_keys
 
  File: authorized_keys
  Size: 1136      Blocks: 8          IO Block: 4096   regula
r file
Device: ca01h/51713dInode: 257561      Links: 1
Access: (0666/-rw-rw-rw-)  Uid: ( 1002/    jane)   Gid: ( 1002/   
 jane)
Access: 2024-02-13 00:34:53.692530853 +0000
Modify: 2024-02-13 00:34:16.005897449 +0000
Change: 2024-02-13 00:34:16.005897449 +0000
 Birth: -
 investigator@ip-10-10-143-60:~$ sudo debsums -c -e
[sudo] password for investigator: 
/etc/sudoers
investigator@ip-10-10-143-60:~$ md5sum /var/tmp/bash
7063c3930affe123baecd3b340f1ad2c  /var/tmp/bash

investigator@ip-10-10-143-60:~$ sudo chkrootkit
ROOTDIR is `/'
Checking `amd'...                                           not fo
und
Checking `basename'...                                      not in
g found
Searching for 64-bit Linux Rootkit modules...               nothin
g found
Searching for Mumblehard Linux ...                          * * * 
* * /var/tmp/findme.sh
investigator@ip-10-10-143-60:~$ sudo rkhunter --check --sk --rwo |
 grep UID