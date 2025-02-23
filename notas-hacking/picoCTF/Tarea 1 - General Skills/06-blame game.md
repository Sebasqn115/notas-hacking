### Descripción
Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/158/challenge.zip)

Hints:
1. In collaborative projects, many users can make many changes. How can you see the changes within one file?
2. Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
3. You can use `python3 <file>.py` to try running the code, though you won't need to for this challenge.

### Solución
Con Webshell

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/158/challenge.zip
--2025-02-23 05:37:54--  https://artifacts.picoctf.net/c_titan/158/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.42, 3.160.5.18, 3.160.5.93, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 294455 (288K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                     100%[==========================================================>] 287.55K  1.84MB/s    in 0.2s    

2025-02-23 05:37:54 (1.84 MB/s) - 'challenge.zip' saved [294455/294455]

Sebas115-picoctf@webshell:~$ ls
challenge.zip
Sebas115-picoctf@webshell:~$ unzip challenge.zip
Sebas115-picoctf@webshell:~$ ls
challenge.zip  drop-in
Sebas115-picoctf@webshell:~$ cd drop-in/
Sebas115-picoctf@webshell:~/drop-in$ ls
message.py
Sebas115-picoctf@webshell:~/drop-in$ cat message.py 
print("Hello, World!"
Sebas115-picoctf@webshell:~/drop-in$ git log

Sebas115-picoctf@webshell:~/drop-in$ git log message.py

```

picoCTF{@sk_th3_1nt3rn_2c6bf174}

Al hacer el git log al mensaje se observa la bandera.

### Notas adicionales


### Referencias
https://webshell.picoctf.org/


