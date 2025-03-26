### Descripción
There is some interesting information hidden around this site [http://mercury.picoctf.net:27393/](http://mercury.picoctf.net:27393/). Can you find it?

Hints:
1. You should have enough hints to find the files, don't run a brute forcer.

### Solución
Inspeccionando la página en el .html encontramos la primer parte de la bandera documentada: 
```
<!-- Here's the first part of the flag: picoCTF{t -->
```

Después debemos ir al archivo .css para encontrar la segunda parte de la bandera: 
```
/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */
```

Luego debemos ir a ver el archivo javascript donde nos muestra lo siguiente: 
```
/* How can I keep Google from indexing my website? */
```

Esto da a entender que hay que buscar en otro lado, en este caso hay que ir a los robots con el link http://mercury.picoctf.net:27393/robots.txt donde encontramos la tercera parte de la bandera:
```
# Part 3: t_0f_pl4c
# I think this is an apache server... can you Access the next flag?
```
Aquí mismo nos da otra pista para encontrar la cuarta parte. En este caso nos dice que vayamos al access, para esto hay que ir al link http://mercury.picoctf.net:27393/.htaccess que nos muestra:
```
# Part 4: 3s_2_lO0k
# I love making websites on my Mac, I can Store a lot of information there.
```
Que nos da otra pista para encontrar la quinta parte y nos da a entender que hay que ir al Store () con link http://mercury.picoctf.net:27393/.DS_Store para encontrar la última parte de la bandera:
```
Congrats! You completed the scavenger hunt. Part 5: _d375c750}
```

Flag:
picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_d375c750}

### Notas adicionales


### Referencias

