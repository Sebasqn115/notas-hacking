### Descripción
Can you break into this super secure portal? `https://jupiter.challenges.picoctf.org/problem/17682/` ([link](https://jupiter.challenges.picoctf.org/problem/17682/)) or http://jupiter.challenges.picoctf.org:17682

Hints:
1. Never trust the client

### Solución
Se inspecciona la página para ver el código y podemos observar que la bandera viene distribuida en 8 partes. En este caso podemos solo seguir el orden de los split, por split, split2, split3, split4, etc e ir juntando cada cadena hasta completar la flag:

picoCTF{no_clients_plz_b706c5}

### Notas adicionales


### Referencias
https://jupiter.challenges.picoctf.org/problem/17682/





