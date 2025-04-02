### Descripción
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). Can you retrieve the flag?

Hints:
1. There is data encoded somewhere... there might be an online decoder.

### Solución
Primero se descarga el archivo:
```
┌──(kali㉿kali)-[~/picoCTF/forensic/whatlieswithin]
└─$ wget 'https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png'
--2025-04-01 19:27:38--  https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 625219 (611K) [application/octet-stream]
Saving to: ‘buildings.png’

buildings.png         100%[======================>] 610.57K   647KB/s    in 0.9s    l

2025-04-01 19:27:39 (647 KB/s) - ‘buildings.png’ saved [625219/625219]

                                                                                     
┌──(kali㉿kali)-[~/picoCTF/forensic/whatlieswithin]
└─$ file buildings.png 
buildings.png: PNG image data, 657 x 438, 8-bit/color RGBA, non-interlaced
```

Después instalamos gem y filtramos la bandera:
```
┌──(kali㉿kali)-[~/picoCTF/forensic/whatlieswithin]
└─$ sudo gem install zsteg                   
[sudo] password for kali: 
Successfully installed zsteg-0.2.13
Parsing documentation for zsteg-0.2.13
Done installing documentation for zsteg after 0 seconds
1 gem installed

──(kali㉿kali)-[~/picoCTF/forensic/whatlieswithin]
└─$ zsteg -a buildings.png | grep picoCTF
b1,rgb,lsb,xy       .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"
```

Flag:
picoCTF{h1d1ng_1n_th3_b1t5}

### Solución 2
Podemos usar la herramienta Steganography Online para decodificar la imagen y que nos muestre la bandera:
![[Imagen de WhatsApp 2025-04-01 a las 17.31.36_e4b2383e.jpg]]

### Notas adicionales


### Referencias
Steganography Online: https://stylesuxx.github.io/steganography/
