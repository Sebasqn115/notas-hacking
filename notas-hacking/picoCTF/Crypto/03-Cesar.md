### Descripción
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/49f31c8f17817dc2d367428c9e5ab0bc/ciphertext).

Hints:
1. caesar cipher [tutorial](https://learncryptography.com/classical-encryption/caesar-cipher)

### Solución
Descargamos el archivo.

```
Sebas115-picoctf@webshell:~/crypto/cesar$ wget https://jupiter.challenges.picoctf.org/static/49f31c8f17817dc2d367428c9e5ab0bc/ciphertext
--2025-05-12 19:45:50--  https://jupiter.challenges.picoctf.org/static/49f31c8f17817dc2d367428c9e5ab0bc/ciphertext
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35 [application/octet-stream]
Saving to: 'ciphertext'

ciphertext                        100%[==========================================================>]      35  --.-KB/s    in 0s      

2025-05-12 19:45:50 (15.6 MB/s) - 'ciphertext' saved [35/35]

Sebas115-picoctf@webshell:~/crypto/cesar$ ls
ciphertext
Sebas115-picoctf@webshell:~/crypto/cesar$ cat ciphertext 
picoCTF{ynkooejcpdanqxeykjrbdofgkq}

```

Utilizando Cyberchef:
```
`Input: ynkooejcpdanqxeykjrbdofgkq`
`Recipe: From ROT13 (rotado 30 veces)`
`Output: crossingtherubiconvfhsjkou`
```
Unimos la bandera.

Flag:
picoCTF{crossingtherubiconvfhsjkou}

### Solución 2
Utilizando un script de python para desencriptar la cadena al aplicar una rotación:

```
import string
import re

abc=string.ascii_letters

encriptado = open('ciphertext','r').read()
encriptado = re.findall('\{(.*?)\}',encriptado)[0]

rot = 30
salida = ''
for car in encriptado:
        salida += abc[ (abc.find(car) + rot) % 26 ]

print("picoCTF{" + salida + "}")


Sebas115-picoctf@webshell:~/crypto/cesar$ python3 exp.py
picoCTF{crossingtherubiconvfhsjkou}
```
### Notas adicionales
Está en cifrado cesar: Es un tipo de cifrado por sustitución donde cada letra del mensaje original (que en criptografía se denomina texto plano) se reemplaza por una letra correspondiente a un cierto número de letras desplazadas hacia arriba o hacia abajo en el alfabeto.

### Referencias
https://privacycanada.net/classical-encryption/caesar-cipher/
https://gchq.github.io/CyberChef