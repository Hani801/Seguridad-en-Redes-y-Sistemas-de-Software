## Objetivo
Embark on the journey of learning the fundamentals of Linux. Learn to run some of the first essential commands on an interactive terminal
## Solución

TASK5:
tryhackme@linux1:~$ ls -r
folder4  folder2  access.log
folder3  folder1
tryhackme@linux1:~$ cat folder4/note
.txt
Hello World!
tryhackme@linux1:~$ ^C
tryhackme@linux1:~$ cat /home/tryhac
kme/folder4
cat: /home/tryhackme/folder4: Is a d
irectory

TASK6:
tryhackme@linux1:~$ grep "THM" access.log
13.127.130.212 - - [04/May/2021:08:35:26 +0000] "GET THM{ACCESS} l
ang=en HTTP/1.1" 404 360 "-" "Mozilla/5.0 (Windows NT 10.0; Win64;
 x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/77.0.3865.120 
Safari/537.36"
## Notas
