### Descripción
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg)

Hints:
1. Wait, you can hide files inside files? But how do you find them?
2. Make sure to submit the flag as picoCTF{XXXXX}

### Solución
Descargar el archivo:

```
┌──(kali㉿kali)-[~/picoCTF/forensic3/matryoshkadoll]
└─$ wget https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg
--2025-04-29 16:23:57--  https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 651632 (636K) [application/octet-stream]
Saving to: ‘dolls.jpg’

dolls.jpg               100%[=============================>] 636.36K  1.22MB/s    in 0.5s    

2025-04-29 16:23:58 (1.22 MB/s) - ‘dolls.jpg’ saved [651632/651632]

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/matryoshkadoll]
└─$ ls
dolls.jpg
```

Ver el archivo con binwalk:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/matryoshkadoll]
└─$ binwalk dolls.jpg  

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 594 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg
651610        0x9F15A         End of Zip archive, footer length: 22
```

Extraer el contenido del archivo con binwalk.
Entrar a la subcarpeta y observar que se tiene.
Entrar a la otra subcarpeta y observar.
Ir haciendo este proceso hasta encontrar el archivo flag.txt y extraerlo con binwalk:
```
──(kali㉿kali)-[~/picoCTF/forensic3/matryoshkadoll]
└─$ binwalk -e dolls.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378952, uncompressed size: 383937, name: base_images/2_c.jpg

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/matryoshkadoll]
└─$ ls
dolls.jpg  _dolls.jpg.extracted
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/matryoshkadoll]
└─$ cd _dolls.jpg.extracted

┌──(kali㉿kali)-[~/picoCTF/forensic3/matryoshkadoll/_dolls.jpg.extracted]
└─$ cd base_images         
                                                                                              
┌──(kali㉿kali)-[~/…/forensic3/matryoshkadoll/_dolls.jpg.extracted/base_images]
└─$ ls
2_c.jpg

┌──(kali㉿kali)-[~/…/forensic3/matryoshkadoll/_dolls.jpg.extracted/base_images]
└─$ binwalk -e 2_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
187707        0x2DD3B         Zip archive data, at least v2.0 to extract, compressed size: 196042, uncompressed size: 201444, name: base_images/3_c.jpg

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented

                                                                                              
┌──(kali㉿kali)-[~/…/forensic3/matryoshkadoll/_dolls.jpg.extracted/base_images]
└─$ ls
2_c.jpg  _2_c.jpg.extracted
                                                                                              
┌──(kali㉿kali)-[~/…/forensic3/matryoshkadoll/_dolls.jpg.extracted/base_images]
└─$ cd _2_c.jpg.extracted  
                                                                                              
┌──(kali㉿kali)-[~/…/matryoshkadoll/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted]
└─$ ls
2DD3B.zip  base_images
                                                                                              
┌──(kali㉿kali)-[~/…/matryoshkadoll/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted]
└─$ cd base_images       
                                                                                              
┌──(kali㉿kali)-[~/…/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ ls
3_c.jpg
                                                                                              
┌──(kali㉿kali)-[~/…/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ binwalk -e 3_c.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
123606        0x1E2D6         Zip archive data, at least v2.0 to extract, compressed size: 77650, uncompressed size: 79807, name: base_images/4_c.jpg

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented

                                                                                              
┌──(kali㉿kali)-[~/…/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ ls
3_c.jpg  _3_c.jpg.extracted
                                                                                              
┌──(kali㉿kali)-[~/…/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ cd _3_c.jpg.extracted 
                                                                                              
┌──(kali㉿kali)-[~/…/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted]
└─$ ls
1E2D6.zip  base_images
                                                                                              
┌──(kali㉿kali)-[~/…/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted]
└─$ cd base_images       
                                                                                              
┌──(kali㉿kali)-[~/…/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ ls
4_c.jpg
                                                                                              
┌──(kali㉿kali)-[~/…/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ binwalk -e 4_c.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
79578         0x136DA         Zip archive data, at least v2.0 to extract, compressed size: 63, uncompressed size: 81, name: flag.txt

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented

                                                                                              
┌──(kali㉿kali)-[~/…/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ ls
4_c.jpg  _4_c.jpg.extracted
                                                                                              
┌──(kali㉿kali)-[~/…/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ cd _                 
cd: no such file or directory: _
                                                                                              
┌──(kali㉿kali)-[~/…/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ cd _4_c.jpg.extracted 
                                                                                              
┌──(kali㉿kali)-[~/…/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted]
└─$ ls
136DA.zip  flag.txt
```


Hacer un cat a la bandera:
```
┌──(kali㉿kali)-[~/…/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted]
└─$ cat flag.txt         
picoCTF{96fac089316e094d41ea046900197662}
```

Flag:
picoCTF{96fac089316e094d41ea046900197662}

### Notas adicionales
Uso de binwalk

### Referencias
