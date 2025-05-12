### Descripción
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf).

Hints:
1. This problem can be solved by just opening the file in different ways

### Solución
Descargamos el archivo .pdf.
Lo abrimos y observamos una parte de la bandera.
Lo mandamos a una imagen haciendo una copia del archivo .pdf pero cambiando el formato a .png para forzarlo a que el archivo sea como una imagen y obtenemos la otra parte de la bandera.
```
Sebas115-picoctf@webshell:~/forensic$ wget https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf
--2025-05-12 07:22:25--  https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3362 (3.3K) [application/octet-stream]
Saving to: 'flag2of2-final.pdf'

flag2of2-final.pdf                100%[==========================================================>]   3.28K  --.-KB/s    in 0s      

2025-05-12 07:22:26 (190 MB/s) - 'flag2of2-final.pdf' saved [3362/3362]

Sebas115-picoctf@webshell:~/forensic$ ls
flag2of2-final.pdf

1n_pn9_&_pdf_249d05c0}

Sebas115-picoctf@webshell:~/forensic$ cp flag2of2-final.pdf flag2of2-final.png

picoCTF{f1u3n7_
```
Finalmente juntamos las 2 partes para formar la bandera.

Flag:
picoCTF{f1u3n7_1n_pn9_&_pdf_249d05c0}
### Notas adicionales


### Referencias
