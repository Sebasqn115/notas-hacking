### Descripción
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?

Hints:
1. The flag is in the format PICOCTF{}

### Solución
Descargamos el archivo png.
Aplicamos un file.
Abrimos la imagen y nos damos cuenta que es la estructura de una bandera pero son todos números.
Es un alfabeto numerado, por lo que una forma de resolverlo es buscar una tabla del alfabeto numerado en google e ir convirtiendo a mano cada uno de los números hasta formar la bandera.
```
Sebas115-picoctf@webshell:~/crypto/thenumbers$ wget https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
--2025-05-12 19:21:06--  https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100721 (98K) [application/octet-stream]
Saving to: 'the_numbers.png'

the_numbers.png                   100%[==========================================================>]  98.36K  --.-KB/s    in 0.04s   

2025-05-12 19:21:06 (2.21 MB/s) - 'the_numbers.png' saved [100721/100721]

Sebas115-picoctf@webshell:~/crypto/thenumbers$ ls
the_numbers.png

Sebas115-picoctf@webshell:~/crypto/thenumbers$ file the_numbers.png 
the_numbers.png: PNG image data, 774 x 433, 8-bit/color RGB, non-interlaced
```


p  i  c  o  C  T  F  {THENUMBERSMASON}
16 9 3 15 3 20 6 {20 8 5 14 21 13 2 5 18 19 13 1 19 15 14}

Flag:
picoCTF{THENUMBERSMASON}

### Solución 2
Usando Cyberchef:
```
`Input: 16 9 3 15 3 20 6 { 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14 }`
`Recipe: From A1Z26 Cypher Decode`
`Output: picoctf.thenumbersmason.`
```

### Notas adicionales


### Referencias
Tabla de alfabeto numerado:
https://www.springboardstories.co.uk/index.php/topics/codes/2505-alphabet-number

Cyberchef:
https://gchq.github.io/CyberChef