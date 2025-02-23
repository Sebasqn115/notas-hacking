### Descripción
How to automate tasks to run at intervals on linux servers?
Additional details will be available after launching your challenge instance.

How to automate tasks to run at intervals on linux servers?Use ssh to connect to this server:

```
Server: saturn.picoctf.net
Port: 63269
Username: picoplayer 
Password: 5wf1w1hVxt
```
### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ ssh -p 63269 picoplayer@saturn.picoctf.net 
The authenticity of host '[saturn.picoctf.net]:63269 ([13.59.203.175]:63269)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:63269' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

picoplayer@challenge:~$ ls
picoplayer@challenge:~$ ls /
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
picoplayer@challenge:~$ ls /root
ls: cannot open directory '/root': Permission denied
picoplayer@challenge:~$ sudo ls /root
[sudo] password for picoplayer: 

Sorry, try again.
[sudo] password for picoplayer: 
Sorry, try again.
[sudo] password for picoplayer: 
picoplayer is not in the sudoers file.  This incident will be reported.
picoplayer@challenge:~$ sudo ls /root
[sudo] password for picoplayer: 
picoplayer is not in the sudoers file.  This incident will be reported.
picoplayer@challenge:~$ sudo ls /challenge/
[sudo] password for picoplayer: 
picoplayer is not in the sudoers file.  This incident will be reported.
picoplayer@challenge:~$ ls /challenge/
ls: cannot open directory '/challenge/': Permission denied
picoplayer@challenge:~$ sudo vi
[sudo] password for picoplayer: 
picoplayer is not in the sudoers file.  This incident will be reported.
picoplayer@challenge:~$ vi 
-bash: vi: command not found
picoplayer@challenge:~$ sudo -l5wf1w1hVxt
sudo: invalid option -- '5'
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user] [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout] [-u user] [VAR=value] [-i|-s]
            [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt] [-T timeout] [-u user] file ...
picoplayer@challenge:~$ sudo -l          
[sudo] password for picoplayer: 
Sorry, user picoplayer may not run sudo on challenge.
picoplayer@challenge:~$ cat challenge
cat: challenge: No such file or directory
picoplayer@challenge:~$ cleara
-bash: cleara: command not found
picoplayer@challenge:~$ ls
picoplayer@challenge:~$ ls /etc/     
adduser.conf            crontab         gshadow      ld.so.conf     mke2fs.conf          python3      shadow       systemd
alternatives            dbus-1          gshadow-     ld.so.conf.d   modules-load.d       python3.8    shadow-      terminfo
apt                     debconf.conf    gss          legal          mtab                 rc0.d        shells       timezone
bash.bashrc             debian_version  host.conf    libaudit.conf  networkd-dispatcher  rc1.d        skel         tmpfiles.d
bindresvport.blacklist  default         hostname     localtime      networks             rc2.d        ssh          ucf.conf
binfmt.d                deluser.conf    hosts        login.defs     nsswitch.conf        rc3.d        ssl          ufw
ca-certificates         dhcp            hosts.allow  logrotate.d    opt                  rc4.d        subgid       update-motd.d
ca-certificates.conf    dpkg            hosts.deny   lsb-release    os-release           rc5.d        subgid-      wgetrc
cloud                   e2scrub.conf    init.d       machine-id     pam.conf             rc6.d        subuid       xattr.conf
cron.d                  environment     inputrc      magic          pam.d                rcS.d        subuid-      xdg
cron.daily              fstab           issue        magic.mime     passwd               resolv.conf  sudoers
cron.hourly             gai.conf        issue.net    mailcap        passwd-              rmt          sudoers.d
cron.monthly            group           kernel       mailcap.order  profile              security     sysctl.conf
cron.weekly             group-          ld.so.cache  mime.types     profile.d            selinux      sysctl.d

picoplayer@challenge:~$ cat /etc/crontab 
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_9d5cb744}
```

picoCTF{Sch3DUL7NG_T45K3_L1NUX_9d5cb744}


### Notas adicionales


### Referencias
https://webshell.picoctf.org/





