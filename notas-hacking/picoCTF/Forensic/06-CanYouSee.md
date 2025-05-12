### Descripción
How about some hide and seek?Download this file [here](https://artifacts.picoctf.net/c_titan/4/unknown.zip).

Hints:
1. How can you view the information about the picture?
2. If something isn't in the expected form, maybe it deserves attention?

### Solución
Descargamos el archivo .zip.
Lo descomprimimos.
Aplicamos un exiftool a la imagen y se nos muestra un texto en base64.
Finalmente, le hacemos un echo para descomprimirlo.
```
Sebas115-picoctf@webshell:~/forensic$ wget https://artifacts.picoctf.net/c_titan/4/unknown.zip
--2025-05-12 07:17:20--  https://artifacts.picoctf.net/c_titan/4/unknown.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2252173 (2.1M) [application/octet-stream]
Saving to: 'unknown.zip'

unknown.zip                       100%[==========================================================>]   2.15M  1.82MB/s    in 1.2s    

2025-05-12 07:17:22 (1.82 MB/s) - 'unknown.zip' saved [2252173/2252173]

Sebas115-picoctf@webshell:~/forensic$ ls
unknown.zip
Sebas115-picoctf@webshell:~/forensic$ unzip unknown.zip 
Archive:  unknown.zip
  inflating: ukn_reality.jpg         
Sebas115-picoctf@webshell:~/forensic$ ls
ukn_reality.jpg  unknown.zip

Sebas115-picoctf@webshell:~/forensic$ exiftool ukn_reality.jpg 
ExifTool Version Number         : 12.40
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.2 MiB
File Modification Date/Time     : 2024:02:15 22:40:14+00:00
File Access Date/Time           : 2025:05:12 07:17:37+00:00
File Inode Change Date/Time     : 2025:05:12 07:17:29+00:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4

Sebas115-picoctf@webshell:~/forensic$ echo cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg== | base64 -d
picoCTF{ME74D47A_HIDD3N_deca06fb}
```

### Solución 2
Lo mandamos a Cyberchef en base64:
```
`Input: cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==`
`Recipe: From base64`
`Output: picoCTF{ME74D47A_HIDD3N_deca06fb}`
```

Flag:
picoCTF{ME74D47A_HIDD3N_deca06fb}

### Notas adicionales


### Referencias
https://gchq.github.io/CyberChef