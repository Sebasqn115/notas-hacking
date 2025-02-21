### Descripción
Run the Python script `code.py` in the same directory as `codebook.txt`.

- [Download code.py](https://artifacts.picoctf.net/c/1/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/1/codebook.txt)

Hints:
1. On the webshell, use `ls` to see if both files are in the directory you are in
2. The `str_xor` function does not need to be reverse engineered for this challenge.

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/1/code.py
--2025-02-20 19:20:14--  https://artifacts.picoctf.net/c/1/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.71, 3.160.5.93, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.71|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: 'code.py'

code.py                           100%[==========================================================>]   1.25K  --.-KB/s    in 0s      

2025-02-20 19:20:14 (1.33 GB/s) - 'code.py' saved [1278/1278]

Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/1/codebook.txt
--2025-02-20 19:20:20--  https://artifacts.picoctf.net/c/1/codebook.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.71, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: 'codebook.txt'

codebook.txt                      100%[==========================================================>]      27  --.-KB/s    in 0s      

2025-02-20 19:20:20 (9.25 MB/s) - 'codebook.txt' saved [27/27]

Sebas115-picoctf@webshell:~$ ls
code.py  codebook.txt
Sebas115-picoctf@webshell:~$ python3 code.py
picoCTF{c0d3b00k_455157_d9aa2df2}
```

picoCTF{c0d3b00k_455157_d9aa2df2}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/


