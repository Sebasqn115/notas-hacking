### Descripción
If you want to hash with the best, beat this test!`nc saturn.picoctf.net 54593``

Hints:
1. You can use a commandline tool or web app to hash text
2. Press Ctrl and c on your keyboard to close your connection and return to the command prompt.

### Solución
Iniciar la prueba con Webshell:

```
Sebas115-picoctf@webshell:~$ nc saturn.picoctf.net 54593
Please md5 hash the text between quotes, excluding the quotes: 'coconuts'
Answer:
```

Se debe de convertir el texto mostrado en hash utilizando la herramienta CyberChef:
```
`Input: coconuts`
`Recipe: MD5`
`Output: 78d1999482f432e9c229269151140542`

Answer:
78d1999482f432e9c229269151140542
Correct.
```

```
Please md5 hash the text between quotes, excluding the quotes: 'money'

`Input: money`
`Recipe: MD5`
`Output: 9726255eec083aa56dc0449a21b33190`

Answer: 
9726255eec083aa56dc0449a21b33190
Correct.

Please md5 hash the text between quotes, excluding the quotes: 'babies'

`Input: babies`
`Recipe: MD5`
`Output: 8374d0764f1466e601c624254222ad53`

Answer: 
8374d0764f1466e601c624254222ad53

```

Después de convertir 3 veces nos muestra la flag:
```
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
```

Flag:
picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
### Notas adicionales

### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef/