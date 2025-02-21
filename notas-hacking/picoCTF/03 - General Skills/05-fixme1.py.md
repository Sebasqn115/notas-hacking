### Descripción
Fix the syntax error in this Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/26/fixme1.py)

Hints:
1. Indentation is very meaningful in Python
2. To view the file in the webshell, do: `$ nano fixme1.py`
3. To exit `nano`, press Ctrl and x and follow the on-screen prompts.
4. The `str_xor` function does not need to be reverse engineered for this challenge.

### Solución
Con Webshell y python3

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/26/fixme1.py
--2025-02-20 19:34:21--  https://artifacts.picoctf.net/c/26/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.93, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py                         100%[==========================================================>]     837  --.-KB/s    in 0s      

2025-02-20 19:34:21 (252 MB/s) - 'fixme1.py' saved [837/837]

Sebas115-picoctf@webshell:~$ ls
fixme1.py
Sebas115-picoctf@webshell:~$ nano fixme1.py 
Sebas115-picoctf@webshell:~$ python3 fixme1.py 
  File "/home/Sebas115-picoctf/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
Sebas115-picoctf@webshell:~$ nano fixme1.py 
Sebas115-picoctf@webshell:~$ python3 fixme1.py 
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_09ee727a}
```

picoCTF{1nd3nt1ty_cr1515_09ee727a}

Con nano se modifica el archivo para arreglar la indentación de la línea de código que imprime la bandera.

### Notas adicionales


### Referencias
https://webshell.picoctf.org/


