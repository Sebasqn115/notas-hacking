### Descripción
Can you get the flag?Go to this [website](http://saturn.picoctf.net:65439/) and see what you can discover.

Hints:
1. How is the password checked on this website?
### Solución
Al inspeccionar la página encontramos una pista que nos manda a login.php, por lo que hay que cambiar la url agregando esto:

```
http://saturn.picoctf.net:65439/login.php
```

Aquí encontramos más código y otra pista de  un archivo secure.js, entonces hacemos lo mismo:
```
http://saturn.picoctf.net:65439/secure.js
```

Y aquí observamos que nos dan el usuario y la contraseña para poder obtener la flag:

```
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}
```

Al logearnos con este usuario admin y la contraseña nos muestra la flag:
```
picoCTF{j5_15_7r4n5p4r3n7_b0c2c9cb}
```

Flag:
picoCTF{j5_15_7r4n5p4r3n7_b0c2c9cb}

### Notas adicionales


### Referencias

