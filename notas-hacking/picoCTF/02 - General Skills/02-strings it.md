### Descripción
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings) without running it?

Hints:
1. [strings](https://linux.die.net/man/1/strings)

### Solución
Con Python

```
Sebas115-picoctf@webshell:~$ wget ~$ https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
Sebas115-picoctf@webshell:~$ file strings   
strings: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=0cdedfba33422d235dba8c90e00fb77b235f1ff8, not stripped
Sebas115-picoctf@webshell:~$ ls -la strings 
-rw-rw-r-- 1 Sebas115-picoctf Sebas115-picoctf 776032 Oct 26  2020 strings
Sebas115-picoctf@webshell:~$ chmod +x strings
Sebas115-picoctf@webshell:~$ ls -la strings 
-rwxrwxr-x 1 Sebas115-picoctf Sebas115-picoctf 776032 Oct 26  2020 strings
Sebas115-picoctf@webshell:~$ ls
README.txt  big-zip-files  big-zip-files.zip  big-zip-files.zip.1  dato  datos  file  flag  hola  strings
Sebas115-picoctf@webshell:~$ ./strings 
Maybe try the 'strings' function? Take a look at the man page
Sebas115-picoctf@webshell:~$ strings strings | grep pico
picoCTF{5tRIng5_1T_7f766a23}
```

picoCTF{5tRIng5_1T_7f766a23}

### Notas adicionales

### Referencias
https://webshell.picoctf.org/
