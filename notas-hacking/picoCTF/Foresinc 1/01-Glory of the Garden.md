### Descripción
This [garden](https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg) contains more than it seems.

Hints:
1. What is a hex editor?

### Solución
Descargar el archivo y usar hexeditor en la imagen para después buscar la cadena especifica "picoCTF":

```
00230560  72 65 20 69  73 20 61 20   66 6C 61 67  20 22 70 69        re is a flag "pi
00230570  63 6F 43 54  46 7B 6D 6F   72 65 5F 74  68 61 6E 5F        coCTF{more_than_
00230580  6D 33 33 74  73 5F 74 68   65 5F 33 79  33 65 42 64        m33ts_the_3y3eBd
00230590  42 64 32 63  63 7D 22 0A                                   Bd2cc}"
```

### Solución 2
Usar un cat garden.jpg:

```
Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"
```

### Solución 3
Usando strings:

```
┌──(kali㉿kali)-[~/picoCTF/forensic/gloryofthegarden]
└─$ strings -n 13 garden.jpg | grep picoCTF
Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"
```

Flag:
picoCTF{more_than_m33ts_the_3y3eBdBd2cc}

### Notas adicionales


### Referencias
