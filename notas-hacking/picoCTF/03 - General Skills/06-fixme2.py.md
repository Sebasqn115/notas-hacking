### Descripción
Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/5/fixme2.py)

Hints:
1. Are equality and assignment the same symbol?
2. To view the file in the webshell, do: `$ nano fixme2.py`
3. To exit `nano`, press Ctrl and x and follow the on-screen prompts.
4. The `str_xor` function does not need to be reverse engineered for this challenge.

### Solución
Con Webshell y python3

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/5/fixme2.py
--2025-02-20 19:40:17--  https://artifacts.picoctf.net/c/5/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.93, 3.160.5.18, 3.160.5.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.93|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py                         100%[==========================================================>]   1.00K  --.-KB/s    in 0s      

2025-02-20 19:40:17 (467 MB/s) - 'fixme2.py' saved [1029/1029]

Sebas115-picoctf@webshell:~$ ls
fixme2.py
Sebas115-picoctf@webshell:~$ python3 fixme2.py 
  File "/home/Sebas115-picoctf/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
Sebas115-picoctf@webshell:~$ nano fixme2.py 
Sebas115-picoctf@webshell:~$ python3 fixme2.py 
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_4863e11b}
```

picoCTF{3qu4l1ty_n0t_4551gnm3nt_4863e11b}

Con nano se modifica el archivo para agregar un signo de igual '=' en la parte que manda el error ya que se trata de una igualdad.

### Notas adicionales


### Referencias
https://webshell.picoctf.org/