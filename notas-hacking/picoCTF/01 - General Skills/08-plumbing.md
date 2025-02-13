### Descripción
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 7480`.`

Hints:
1. Remember the flag format is picoCTF{XXXX}
2. What's a pipe? No not that kind of pipe... This [kind](http://www.linfo.org/pipes.html)

### Solución
Con Webshell
```
`Sebas115-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 7480 | grep picoCTF`
`picoCTF{digital_plumb3r_06e9d954}`
```


### Solución
Con Webshell
```
Sebas115-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 7480 > datos

Sebas115-picoctf@webshell:~$ cat datos | grep pico
picoCTF{digital_plumb3r_06e9d954}
```

### Notas adicionales
El servidor de nc contiene información desordenada que evita ver la flag a primera vista.
Mediante | utilizado como tubería y con el comando grep y especificando la palabra "picoCTF" se hace una busqueda en la salida de nc para obtener la cadena que contenga la palabra "picoCTF" la cual es la flag que estamos buscando.

### Referencias
https://webshell.picoctf.org/