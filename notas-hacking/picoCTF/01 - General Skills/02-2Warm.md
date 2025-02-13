### Descripción
Can you convert the number 42 (base 10) to binary (base 2)?

Hints:
1. Submit your answer in our competition's flag format. For example, if your answer was '11111', you would submit 'picoCTF{11111}' as the flag.

### Solución
Con Python

```
`Sebas115-picoctf@webshell:~$ python`
`Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux`
`Type "help", "copyright", "credits" or "license" for more information.`
>>> `bin(42)`
`'0b101010'`
```

**Solución 2**
Usando cyberchef https://gchq.github.io/CyberChef

```
`Input: 42`
`Recipe: From base 10 To base 2`
`Output: 101010`
```

### Notas adicionales

Se puede hacer también de la siguiente manera. 
Usando cyberchef https://gchq.github.io/CyberChef

```
`Input: 42`
`Recipe: From decimal, To binary`
`Output: 101010`
```

### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef