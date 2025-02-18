### Descripción
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 15130`.

Hints:
1. I hear python can convert things.
2. It might help to have multiple windows open.

### Solución
Con Python

```
Sebas115-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 15130
Let us see how data is stored
pie
Please give the 01110000 01101001 01100101 as a word.
...
you have 45 seconds.....

Input:
pie
Please give me the  163 165 142 155 141 162 151 156 145 as a word.
Input:
submarine
Please give me the 706965 as a word.
Input:
pie
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_02167de8}
```

Usando cyberchef https://gchq.github.io/CyberChef

```
`Input: 01110000 01101001 01100101`
`Recipe: From Binary`
`Output: pie`

`Input: 163 165 142 155 141 162 151 156 145`
`Recipe: From Octal`
`Output: submarine`

`Input: 706965`
`Recipe: From Hex`
`Output: pie`
```

picoCTF{learning_about_converting_values_02167de8}

### Notas adicionales

### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef


