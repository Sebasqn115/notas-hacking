### Descripción
Help us test the form by submiting the username as `test` and password as `test!`The website running [here](http://saturn.picoctf.net:62263/).

Hints:
1. any redirections?

### Solución
Entramos a la página e introducimos el usuario y la contraseña que nos dieron.
Al parecer al hacer login se pasa por 2 procesos, ya que al retroceder de página primero nos muestra una con el siguiente link:
```
http://saturn.picoctf.net:62263/next-page/id=bF90aGVfd2F5X2EwZmUwNzRmfQ==
```

Y si volvemos a retroceder nos manda a la siguiente:
```
http://saturn.picoctf.net:62263/next-page/id=cGljb0NURntwcm94aWVzX2Fs 
```

De estos 2 links podemos obtener las 2 cadenas que están después del id= y podemos juntarlas para decodificarlas en base 64:
```
cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5X2EwZmUwNzRmfQ==
```

En CyberChef:
```
`Input: cGljb0NURntwcm94aWVzX2FsbF90aGVfd2F5X2EwZmUwNzRmfQ==`
`Recipe: From Base64`
`Output: picoCTF{proxies_all_the_way_a0fe074f}`
```

Flag:
picoCTF{proxies_all_the_way_a0fe074f}
### Notas adicionales

### Referencias
https://gchq.github.io/CyberChef/