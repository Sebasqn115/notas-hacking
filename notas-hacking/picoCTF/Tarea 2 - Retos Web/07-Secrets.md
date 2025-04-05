### Descripción
We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:64978/).

Hints:
1. folders folders folders
### Solución
Inspeccionando la página encontramos una pista para acceder a un url con secret:

```
http://saturn.picoctf.net:64978/secret/
```

Aquí encontramos otra para  ir a hidden:
```
http://saturn.picoctf.net:64978/secret/hidden/
```

Aquí otra más para ir a superhidden:

```
http://saturn.picoctf.net:64978/secret/hidden/superhidden/
```

Y al inspeccionar este ultimo sitio encontramos la flag: 
```
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" href="mycss.css" />
  </head>

  <body>
    <h1>Finally. You found me. But can you see me</h1>
    <h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_51b260fe}</h3>
  </body>
</html>
```

Flag:
picoCTF{succ3ss_@h3n1c@10n_51b260fe}

### Notas adicionales


### Referencias

