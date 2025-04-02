### Descripción
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?

Hints:
1. How do operating systems know what kind of file it is? (It's not just the ending!
2. Make sure to submit the flag as picoCTF{XXXXX}

### Solución
Primero descargamos el archivo:
```
┌──(kali㉿kali)-[~/picoCTF/forensic/extensions]
└─$ wget 'https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt'
--2025-04-01 19:21:05--  https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9984 (9.8K) [application/octet-stream]
Saving to: ‘flag.txt’

flag.txt              100%[======================>]   9.75K  --.-KB/s    in 0s      

2025-04-01 19:21:06 (367 MB/s) - ‘flag.txt’ saved [9984/9984]
```

Luego es necesario ver el tipo de archivo que es:
```
┌──(kali㉿kali)-[~/picoCTF/forensic/extensions]
└─$ file flag.txt    
flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced
```

Aquí observamos que es un archivo PNG por lo que es necesario cambial la extensión de .txt a .png para poder abrir la imagen:
```
┌──(kali㉿kali)-[~/picoCTF/forensic/extensions]
└─$ mv flag.txt flag.png
                                                                                     
┌──(kali㉿kali)-[~/picoCTF/forensic/extensions]
└─$ open flag.png
```
Al abrir la imagen se nos muestra la bandera, solo que en este caso no se puede copiar por lo que es mejor transcribirla:

Flag:
picoCTF{now_you_know_about_extensions}

### Notas adicionales


### Referencias

