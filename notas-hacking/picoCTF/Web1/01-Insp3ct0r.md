### Descripción
Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/9670/` ([link](https://jupiter.challenges.picoctf.org/problem/9670/)) or http://jupiter.challenges.picoctf.org:9670

Hints:
1. How do you inspect web code on a browser?
2. There's 3 parts

### Solución
Inspeccionando cada parte de código:

En html encontramos la primer parte de la flag:
```
<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
```

En css encontramos la segunda parte de la flag:
```
/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
```

En javascript encontramos la tercera parte de la flag:
```
/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?2e7b23e3} */
```

picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}

### Notas adicionales


### Referencias
https://jupiter.challenges.picoctf.org/problem/9670/
