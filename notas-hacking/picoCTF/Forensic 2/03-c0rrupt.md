### Descripción
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.

Hints:
1. Try fixing the file header

### Solución
Primero se descarga el archivo:
```
──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ wget https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery
--2025-04-08 13:25:11--  https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 202940 (198K) [application/octet-stream]
Saving to: ‘mystery’

mystery                        100%[==================================================>] 198.18K  1.03MB/s    in 0.2s    

2025-04-08 13:25:11 (1.03 MB/s) - ‘mystery’ saved [202940/202940]
```

Y observamos el archivo:
```
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ file mystery 
mystery: data
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ xxd mystery | head
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ hexeditor mystery 
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ file mystery 
mystery: data
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ hexeditor mystery
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ file mystery 
mystery: PNG image data, 1642 x 1095, 8-bit/color RGB, non-interlaced
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ open mystery
```

Instalamos la herramienta pngcheck y la usamos en el archivo:
```
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ sudo apt install pngcheck 
[sudo] password for kali: 
Error: Unable to locate package pngcheck
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ sudo apt update          
Get:1 http://kali.download/kali kali-rolling InRelease [41.5 kB]
Get:2 http://kali.download/kali kali-rolling/main amd64 Packages [20.8 MB]
Get:3 http://kali.download/kali kali-rolling/main amd64 Contents (deb) [50.6 MB]                                         
Get:4 http://kali.download/kali kali-rolling/contrib amd64 Packages [119 kB]                                             
Get:5 http://kali.download/kali kali-rolling/contrib amd64 Contents (deb) [326 kB]                                       
Get:6 http://kali.download/kali kali-rolling/non-free amd64 Packages [201 kB]                                            
Get:7 http://kali.download/kali kali-rolling/non-free amd64 Contents (deb) [882 kB]                                      
Get:8 http://kali.download/kali kali-rolling/non-free-firmware amd64 Packages [10.6 kB]                                  
Get:9 http://kali.download/kali kali-rolling/non-free-firmware amd64 Contents (deb) [24.3 kB]                            
Fetched 73.0 MB in 28s (2,593 kB/s)                                                                                      
1644 packages can be upgraded. Run 'apt list --upgradable' to see them.

┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ sudo apt install pngcheck

Installing:                     
  pngcheck
```

El archivo tiene encabezados dañados.
Hay algunos bits que identifican el tipo de archivo y su estructura, el archivo no los tiene bien.
Se corrigen estos encabezados con hexeditor, pero esto no funciona aún.
Después de los encabezados vienen los chunks que también hay que corregir algunos mediante códigos hexadecimales para que funcionen.
Observamos que sigue habiendo un error en algun chunck, ya que el tamaño de la imagen es muy grande. Después de corregir esto observamos que ahora el chunck DET está mal ya que tiene una longitud muy grande.

Corrección de encabezados y chunks:
```
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ pngcheck -v mystery 
zlib warning:  different version (expected 1.2.13, using 1.3.1)

File: mystery (202940 bytes)
  chunk IHDR at offset 0x0000c, length 13
    1642 x 1095 image, 24-bit RGB, non-interlaced
  chunk sRGB at offset 0x00025, length 1
    rendering intent = perceptual
  chunk gAMA at offset 0x00032, length 4: 0.45455
  chunk pHYs at offset 0x00042, length 9: 2852132389x5669 pixels/meter
  CRC error in chunk pHYs (computed 38d82c82, expected 495224f0)
ERRORS DETECTED in mystery
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ hexeditor mystery 
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ pngcheck -v mystery
zlib warning:  different version (expected 1.2.13, using 1.3.1)

File: mystery (202940 bytes)
  chunk IHDR at offset 0x0000c, length 13
    1642 x 1095 image, 24-bit RGB, non-interlaced
  chunk sRGB at offset 0x00025, length 1
    rendering intent = perceptual
  chunk gAMA at offset 0x00032, length 4: 0.45455
  chunk pHYs at offset 0x00042, length 9: 5669x5669 pixels/meter (144 dpi)
:  invalid chunk length (too large)
ERRORS DETECTED in mystery
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ hexeditor mystery  
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ pngcheck -v mystery
zlib warning:  different version (expected 1.2.13, using 1.3.1)

File: mystery (202940 bytes)
  chunk IHDR at offset 0x0000c, length 13
    1642 x 1095 image, 24-bit RGB, non-interlaced
  chunk sRGB at offset 0x00025, length 1
    rendering intent = perceptual
  chunk gAMA at offset 0x00032, length 4: 0.45455
  chunk pHYs at offset 0x00042, length 9: 5669x5669 pixels/meter (144 dpi)
:  invalid chunk length (too large)
ERRORS DETECTED in mystery
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ hexeditor mystery  
                                                                                                                          
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ pngcheck -v mystery
zlib warning:  different version (expected 1.2.13, using 1.3.1)

File: mystery (202940 bytes)
  chunk IHDR at offset 0x0000c, length 13
    1642 x 1095 image, 24-bit RGB, non-interlaced
  chunk sRGB at offset 0x00025, length 1
    rendering intent = perceptual
  chunk gAMA at offset 0x00032, length 4: 0.45455
  chunk pHYs at offset 0x00042, length 9: 5669x5669 pixels/meter (144 dpi)
:  invalid chunk length (too large)
ERRORS DETECTED in mystery
                                                                                                                         
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ pngcheck -v mystery
zlib warning:  different version (expected 1.2.13, using 1.3.1)

File: mystery (202940 bytes)
  chunk IHDR at offset 0x0000c, length 13
    1642 x 1095 image, 24-bit RGB, non-interlaced
  chunk sRGB at offset 0x00025, length 1
    rendering intent = perceptual
  chunk gAMA at offset 0x00032, length 4: 0.45455
  chunk pHYs at offset 0x00042, length 9: 5669x5669 pixels/meter (144 dpi)
:  invalid chunk length (too large)
ERRORS DETECTED in mystery
                                                                                                                         
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ hexeditor mystery  
                                                                                                                         
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ pngcheck -v mystery
zlib warning:  different version (expected 1.2.13, using 1.3.1)

File: mystery (202940 bytes)
  chunk IHDR at offset 0x0000c, length 13
    1642 x 1095 image, 24-bit RGB, non-interlaced
  chunk sRGB at offset 0x00025, length 1
    rendering intent = perceptual
  chunk gAMA at offset 0x00032, length 4: 0.45455
  chunk pHYs at offset 0x00042, length 9: 5669x5669 pixels/meter (144 dpi)
  chunk IDAT at offset 0x00057, length 65445
    zlib: deflated, 32K window, fast compression
  chunk IDAT at offset 0x10008, length 65524
  chunk IDAT at offset 0x20008, length 65524
  chunk IDAT at offset 0x30008, length 6304
  chunk IEND at offset 0x318b4, length 0
No errors detected in mystery (9 chunks, 96.3% compression).
                                                                                                                         
┌──(kali㉿kali)-[~/picoCTF/forensic2/corrupt]
└─$ open mystery
```

Al tener todo corregido ahora si intentamos abrir la imagen y se nos muestra la bandera.
Flag:
picoCTF{c0rrupt10n_1847995}

### Notas adicionales


### Referencias
Herramienta pngcheck
https://en.wikipedia.org/wiki/PNG