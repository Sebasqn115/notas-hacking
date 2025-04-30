### Descripción
We found this [file](https://mercury.picoctf.net/static/da18eed3d15fd04f7b076bdcecf15b27/tunn3l_v1s10n). Recover the flag.

Hints:
1. Weird that it won't display right...

### Solución
Descargar el archivo y observar su tipo:

```
descargar archivo y ver que tipo es: ┌──(kali㉿kali)-[~/picoCTF/forensic3/tunnelvision]
└─$ wget https://mercury.picoctf.net/static/da18eed3d15fd04f7b076bdcecf15b27/tunn3l_v1s10n
--2025-04-30 00:13:06--  https://mercury.picoctf.net/static/da18eed3d15fd04f7b076bdcecf15b27/tunn3l_v1s10n
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2893454 (2.8M) [application/octet-stream]
Saving to: ‘tunn3l_v1s10n’

tunn3l_v1s10n           100%[=============================>]   2.76M  1.14MB/s    in 2.4s    

2025-04-30 00:13:09 (1.14 MB/s) - ‘tunn3l_v1s10n’ saved [2893454/2893454]

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/tunnelvision]
└─$ ls
tunn3l_v1s10n
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/tunnelvision]
└─$ file tunn3l_v1s10n 
tunn3l_v1s10n: data
```

Abrir el archivo con el editor hexadecimal y cambiar los bytes correctamente en hexadecimal:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/tunnelvision]
└─$ hexeditor tunn3l_v1s10n
```

Corregir el offset donde inician los datos.
Cambiar el alto de la imagen para ver que más tiene. En este caso se observa la imagen completa y la bandera en la parte superior.
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/tunnelvision]
└─$ hexeditor tunn3l_v1s10n
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/tunnelvision]
└─$ open tunn3l_v1s10n
```


Flag:
picoCTF{qu1t3_a_v13w_2020}

### Notas adicionales
Lo que se hizo fue cambiar bytes para poder abrir la imagen y después configurar su alto para verla correctamente y encontrar la flag con ayuda de hexeditor.

### Referencias
https://en.wikipedia.org/wiki/List_of_file_signatures