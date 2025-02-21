### Descripción
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/14/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/14/level2.flag.txt.enc) in the same directory too.

Hints:
1. Does that encoding look familiar?
2. The `str_xor` function does not need to be reverse engineered for this challenge.

### Solución
Con Webshell, python y python3

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/14/level2.py
--2025-02-20 19:56:56--  https://artifacts.picoctf.net/c/14/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.93, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py                         100%[==========================================================>]     914  --.-KB/s    in 0s      

2025-02-20 19:56:56 (718 MB/s) - 'level2.py' saved [914/914]

Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/14/level2.flag.txt.enc
--2025-02-20 19:57:01--  https://artifacts.picoctf.net/c/14/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.71, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc               100%[==========================================================>]      31  --.-KB/s    in 0s      

2025-02-20 19:57:01 (1.15 MB/s) - 'level2.flag.txt.enc' saved [31/31]

Sebas115-picoctf@webshell:~$ ls
level2.flag.txt.enc  level2.py
Sebas115-picoctf@webshell:~$ nano level2.py
Sebas115-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x34) + chr(0x65) + chr(0x63) + chr(0x39)
'4ec9'
>>>
Sebas115-picoctf@webshell:~$ python3 level2.py 
Please enter correct password for flag: 4ec9
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_9701e681}

```

picoCTF{tr45h_51ng1ng_9701e681}


**Solución 2**
Usando cyberchef https://gchq.github.io/CyberChef

```
`Input: 0x34 0x65 0x63 0x39`
`Recipe: From Hex`
`Output: 4ec9`
```

### Notas adicionales


### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef