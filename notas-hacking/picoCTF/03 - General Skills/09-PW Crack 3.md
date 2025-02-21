### Descripción
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/17/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/17/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/17/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

Hints:
1. To view the level3.hash.bin file in the webshell, do: `$ bvi level3.hash.bin`
2. To exit `bvi` type `:q` and press enter.
3. The `str_xor` function does not need to be reverse engineered for this challenge.

### Solución
Con Webshell y python3

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.py
--2025-02-20 20:07:10--  https://artifacts.picoctf.net/c/17/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.18, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py                         100%[==========================================================>]   1.31K  --.-KB/s    in 0s      

2025-02-20 20:07:11 (1.19 GB/s) - 'level3.py' saved [1337/1337]

Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.flag.txt.enc
--2025-02-20 20:07:15--  https://artifacts.picoctf.net/c/17/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.71, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.enc               100%[==========================================================>]      31  --.-KB/s    in 0s      

2025-02-20 20:07:15 (18.8 MB/s) - 'level3.flag.txt.enc' saved [31/31]

Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.hash.bin
--2025-02-20 20:07:18--  https://artifacts.picoctf.net/c/17/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.42, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin                   100%[==========================================================>]      16  --.-KB/s    in 0s      

2025-02-20 20:07:18 (10.5 MB/s) - 'level3.hash.bin' saved [16/16]

Sebas115-picoctf@webshell:~$ ls   
level3.flag.txt.enc  level3.hash.bin  level3.py
Sebas115-picoctf@webshell:~$ bvi level3.hash.bin 

bvi version 1.4.0 Copyright (C) 1996-2014 by Gerhard Buergmann
Sebas115-picoctf@webshell:~$ nano level3.py
Sebas115-picoctf@webshell:~$ python3 level3.py 
Please enter correct password for flag: 87ab
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_cd6ed2eb}

```

picoCTF{m45h_fl1ng1ng_cd6ed2eb}

Al entrar al código con nano nos muestra 7 posibles contraseñas, por lo que se fue probando cada una hasta encontrar la indicada y así obtener la bandera. 


### Notas adicionales


### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef
