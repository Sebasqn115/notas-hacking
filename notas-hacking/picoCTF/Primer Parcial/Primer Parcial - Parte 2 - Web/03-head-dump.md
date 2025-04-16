### Descripción
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.The website is running [picoCTF News](http://verbal-sleep.picoctf.net:51000/).

Hints:
1. Explore backend development with us
2. The head was dumped.

### Solución
Entramos a la página y nos vamos a la documentación de API.
Aqui nos vamos al apartado de Diagnosing y elegimos el que dice "/heapdump" y damos en execute.
Esto nos manda un archivo que podemos descargar y en el cual podemos buscar la palabra "picoCTF{" y nos manda directamente a la línea que contiene la bandera:

```
277020 picoCTF{Pat!3nt_15_Th3_K3y_305d5b9a}
```


### Notas adicionales

### Referencias
