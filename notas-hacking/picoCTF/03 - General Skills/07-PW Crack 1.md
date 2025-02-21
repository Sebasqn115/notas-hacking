### Descripción
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/10/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/10/level1.flag.txt.enc) in the same directory too.

Hints:
1. To view the file in the webshell, do: `$ nano level1.py`
2. To exit `nano`, press Ctrl and x and follow the on-screen prompts.
3. The `str_xor` function does not need to be reverse engineered for this challenge.

### Solución
Con Webshell y python3

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/10/level1.py
--2025-02-20 19:48:10--  https://artifacts.picoctf.net/c/10/level1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.42, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 876 [application/octet-stream]
Saving to: 'level1.py'

level1.py                         100%[==========================================================>]     876  --.-KB/s    in 0s      

2025-02-20 19:48:11 (37.4 MB/s) - 'level1.py' saved [876/876]

Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/10/level1.flag.txt.enc
--2025-02-20 19:48:15--  https://artifacts.picoctf.net/c/10/level1.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.18, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30 [application/octet-stream]
Saving to: 'level1.flag.txt.enc'

level1.flag.txt.enc               100%[==========================================================>]      30  --.-KB/s    in 0s      

2025-02-20 19:48:15 (883 KB/s) - 'level1.flag.txt.enc' saved [30/30]

Sebas115-picoctf@webshell:~$ ls
level1.flag.txt.enc  level1.py

Sebas115-picoctf@webshell:~$ python3 level1.py 
Please enter correct password for flag: 
That password is incorrect

Sebas115-picoctf@webshell:~$ nano level1.py
Sebas115-picoctf@webshell:~$ python3 level1.py 
Please enter correct password for flag: 691d
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_56891419}

```

picoCTF{545h_r1ng1ng_56891419}

Se usa nano para observar el código y en una función dentro del if se puede observar la contraseña para obtener la bandera.

### Notas adicionales


### Referencias
https://webshell.picoctf.org/