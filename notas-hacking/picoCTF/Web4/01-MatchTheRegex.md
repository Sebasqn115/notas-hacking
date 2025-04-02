### Descripción
How about trying to match a regular expressionThe website is running [here](http://saturn.picoctf.net:53226/).

Hints:
1. Access the webpage and try to match the regular expression associated with the text field

### Solución
Al observar el código fuente observamos una expresión regular la cual es la que se valida. Hay que usar RegExr y mandar la expresión para buscar un texto que coincida con la expresión. RegExr nos da pistas para sacar el texto. El texto es:
```
p12345F
```
Debe comenzar con p, tener 5 caracteres de los que sean y terminar con F.

Al mandar ese texto a la página nos manda la bandera:
```
picoCTF{succ3ssfully_matchtheregex_8ad436ed}
```

Flag:
picoCTF{succ3ssfully_matchtheregex_8ad436ed}

### Notas adicionales


### Referencias
https://regexr.com/