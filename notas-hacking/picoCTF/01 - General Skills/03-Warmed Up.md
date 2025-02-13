### Descripción
What is 0x3D (base 16) in decimal (base 10)?`

Hints:
1. Submit your answer in our flag format. For example, if your answer was '22', you would submit 'picoCTF{22}' as the flag.

### Solución
Con Webshell
```
`Sebas115-picoctf@webshell:~$ python`
`Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux`
`Type "help", "copyright", "credits" or "license" for more information.`
>>> `int(0x3D)`
`61`
```

**Solución 2**
Usando cyberchef https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')&input=MHg3MA

```
`Input: 0x3D`
`Recipe: To Base 10`
`Output: 61`
```

### Notas adicionales


### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef/#recipe=To_Base(10)&input=MHgzRA&ieol=CRLF&oeol=CRLF