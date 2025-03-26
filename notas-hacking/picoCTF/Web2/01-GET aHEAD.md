### Descripción
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:15931/](http://mercury.picoctf.net:15931/)

Hints:
1. Maybe you have more than 2 choices
2. Check out tools like Burpsuite to modify your requests and look at the responses

### Solución
Utilizando Burp Suite para poder penetrar en la página web.
Al interceptar la señal y hacer que reciba algún GET o POST se muestra en la aplicación la información de está señal:

```
GET /index.php? HTTP/1.1
Host: mercury.picoctf.net:15931
Accept-Language: es-419,es;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://mercury.picoctf.net:15931/index.php
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
```

Al cambiar el método de petición actual a 'HEAD' se devuelven los encabezados de la respuestas y no el cuerpo, es decir, se obtienen otros datos de la página web que en esté caso nos muestran la bandera:

```
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_82880908}
Content-type: text/html; charset=UTF-8
```

picoCTF{r3j3ct_th3_du4l1ty_82880908}


### Solución
Usando Webshell:
```
Sebas115-picoctf@webshell:~$ curl -I http://mercury.picoctf.net:15931/index.php
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_82880908}
Content-type: text/html; charset=UTF-8
```

Aquí nos manda la bandera:
picoCTF{r3j3ct_th3_du4l1ty_82880908}
### Notas adicionales
Para que funcionara de manera correcta la primera solución se activó la opción para poder interceptar respuestas según el HEADER.

### Solución 3
Usando BurpSuite al mandar la señal POST al repetidor se hace el cambio de la petición a 'HEAD' y se manda para que devuelva la flag:

![[Pasted image 20250325123653.png]]

### Referencias
Herramienta: Blurp Suite
https://webshell.picoctf.org/