### Descripción
Our flag printing service has started glitching!
Additional details will be available after launching your challenge instance.

Our flag printing service has started glitching!`$ nc saturn.picoctf.net 52969`

Hints:
1. ASCII is one of the most common encodings used in programming
2. We know that the glitch output is valid Python, somehow!
3. Press Ctrl and c on your keyboard to close your connection and return to the command prompt.

### Solución
Con Webshell
```
`Sebas115-picoctf@webshell:~$ nc saturn.picoctf.net 53777`
`'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'`
```

Con Python
```
`Sebas115-picoctf@webshell:~$ python`
`Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux`
`Type "help", "copyright", "credits" or "license" for more information.`
>>> `chr(0x62)`
`'b'`
>>> `chr(0x64)`
`'d'`
>>> `chr(0x61)`
`'a'`
>>> `chr(0x36)`
`'6'`
>>> `chr(0x38)`
`'8'`
>>> `chr(0x66)`
`'f'`
>>> `chr(0x37)`
`'7'`
>>> `chr(0x35)`
`'5'`
```

Finalmente se junta la primera parte obtenida de webshell: gl17ch_m3_n07_
Con los caracteres obtenidos de cada base en python: bda68f75
Resultado: gl17ch_m3_n07_bda68f75

### Notas adicionales

Se puede poner toda la cadena en python.
```
Sebas115-picoctf@webshell:~$ nc saturn.picoctf.net 61813
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
^C      
Sebas115-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
'picoCTF{gl17ch_m3_n07_bda68f75}'
```

### Referencias
https://webshell.picoctf.org/