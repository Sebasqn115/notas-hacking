### Descripción
Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/504/big-zip-files.zip)

Hints:
1. Can grep be instructed to look at every file in a directory and its subdirectories?

### Solución
Con Python

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/504/big-zip-files.zip
Sebas115-picoctf@webshell:~$ unzip big-zip-files.zip

Sebas115-picoctf@webshell:~$ grep -R picoCTF{
.python_history:Sebas115-picoctf@webshell:~$ picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}
.python_history:-bash: picoCTF{gl17ch_m3_n07_ + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + }: command not found
.python_history:'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
.python_history:'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
.python_history:'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}

picoCTF{gr3p_15_m4g1c_ef8790dc}
```

Mediante el comando grep -R se busca la cadena picoCTF{ dentro de todos los directorios y subdirectorios. Esto facilita la búsqueda, ya que son demasiados subdirectorios los que se generaron al descomprimir el archivo.

picoCTF{gr3p_15_m4g1c_ef8790dc}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/