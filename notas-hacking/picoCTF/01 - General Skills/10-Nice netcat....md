### Descripción
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 43239`, but it doesn't speak English...`

Hints:
1. You can practice using netcat with this picoGym problem: [what's a netcat?](https://play.picoctf.org/practice/challenge/34)
2. You can practice reading and writing ASCII with this picoGym problem: [Let's Warm Up](https://play.picoctf.org/practice/challenge/22)

### Solución
Con Webshell

```
`Sebas115-picoctf@webshell:~$ nc mercury.picoctf.net 43239`
`112` 
`105` 
`99` 
`111` 
`67` 
`84` 
`70` 
`123` 
`103` 
`48` 
`48` 
`100` 
`95` 
`116` 
`116` 
`121` 
`33` 
`95` 
`55` 
`99` 
`48` 
`56` 
`50` 
`49` 
`102` 
`53` 
`125` 
`10
`107` 
`49` 
`116` 
`116` 
`121` 
`33` 
`95` 
`110` 
`49` 
`99` 
`51` 
`95` 
`107` 
`49` `
```

**Con ASCII.es**
Después se pasa este ASCII codificado a un conversor de ASCII a Texto y devuelve la flag:
picoCTF{g00d_k1tty!_n1c3_k1tty!_7c0821f5}


### Solución 2
Con Cyberchef https://gchq.github.io/CyberChef

```
`Input: 112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
55 
99 
48 
56 
50 
49 
102 
53 
125 
10 `
`Recipe: From decimal`
`Output: picoCTF{g00d_k1tty!_n1c3_k1tty!_7c0821f5}`
```


### Notas adicionales

### Referencias
https://webshell.picoctf.org/
https://ascii.es/conversor-texto-ascii/
https://gchq.github.io/CyberChef