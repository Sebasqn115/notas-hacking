### Descripción
Every file gets a flag.The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/256/flag.png).

### Solución
Descargar el archivo flag.png.
Al abrirlo no observamos nada relevante.
Al hacer un zsteg -a al archivo nos dice que hay datos ocultos empaquetados en la imagen.
Aplicamos binwalk -e a la imagen para extraer los archivos ocultos de la imagen.
Entramos a la carpeta extraída y al directorio secret donde encontramos otra imagen la cual al abrirla nos muestra la bandera:
```
Sebas115-picoctf@webshell:~/forensic$ wget https://artifacts.picoctf.net/c/256/flag.png
--2025-05-12 07:00:24--  https://artifacts.picoctf.net/c/256/flag.png
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 43058 (42K) [application/octet-stream]
Saving to: 'flag.png'

flag.png                          100%[==========================================================>]  42.05K  --.-KB/s    in 0.02s   

2025-05-12 07:00:24 (2.04 MB/s) - 'flag.png' saved [43058/43058]

Sebas115-picoctf@webshell:~/forensic$ zsteg -a flag.png 
[?] 3319 bytes of extra data after image end (IEND), offset = 0x9b3b
extradata:0         .. file: Zip archive data, at least v1.0 to extract, compression method=store

Sebas115-picoctf@webshell:~/forensic$ binwalk -e flag.png 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 512 x 504, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, compressed
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2997, uncompressed size: 3152, name: secret/flag.png
43036         0xA81C          End of Zip archive, footer length: 22

Sebas115-picoctf@webshell:~/forensic$ ls
_flag.png.extracted  flag.png
Sebas115-picoctf@webshell:~/forensic$ cd _flag.png.extracted/
Sebas115-picoctf@webshell:~/forensic/_flag.png.extracted$ ls
29  29.zlib  9B3B.zip  secret
Sebas115-picoctf@webshell:~/forensic/_flag.png.extracted$ cd secret/
Sebas115-picoctf@webshell:~/forensic/_flag.png.extracted/secret$ ls
flag.png

```


Flag:
picoCTF{Hiddinng_An_imag3_within_@n_ima9e_85e04ab8}
### Notas adicionales


### Referencias
