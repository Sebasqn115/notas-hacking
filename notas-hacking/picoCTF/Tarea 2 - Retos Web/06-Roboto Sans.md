### Descripción
The flag is somewhere on this web application not necessarily on the website. Find it.Check [this](http://saturn.picoctf.net:50361/) out.

### Solución
El sitio web como tal no muestra ninguna pista. Vamos a ir a checar el robots.txt modificando la url:

```
http://saturn.picoctf.net:50361/robots.txt
```

Donde nos muestra lo siguiente:
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```

Este conjunto de letras extrañas está en base64 por lo que es necesario desencriptarlo mediante Cyberchef y al hacerlo nos muestra:
```
`Input: anMvbXlmaWxlLnR4dA==`
`Recipe: From Base64`
`Output: js/myfile.txt`
```

Esto nos da otra pista en la cual es necesario volver a modificar la url para ver que nos manda:

```
picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}
```
Esto finalmente nos muestra la flag.

Flag:
picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}

### Notas adicionales


### Referencias
Cyberchef: https://gchq.github.io/CyberChef
