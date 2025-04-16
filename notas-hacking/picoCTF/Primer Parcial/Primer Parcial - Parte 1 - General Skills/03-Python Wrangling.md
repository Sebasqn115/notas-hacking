### Descripción
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/ende.py) using [this password](https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/pw.txt) to get [the flag](https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/flag.txt.en)?

Hints:
1. Get the Python script accessible in your shell by entering the following command in the Terminal prompt: `$ wget https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/ende.py`
2. `$ man python`

### Solución
Se descargan los 3 archivos:

```
Sebas115-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/ende.py
--2025-04-15 20:16:18--  https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/ende.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1328 (1.3K) [application/octet-stream]
Saving to: 'ende.py'

ende.py                           100%[==========================================================>]   1.30K  --.-KB/s    in 0s      

2025-04-15 20:16:18 (438 MB/s) - 'ende.py' saved [1328/1328]

Sebas115-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/pw.txt
--2025-04-15 20:16:26--  https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/pw.txt
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33 [application/octet-stream]
Saving to: 'pw.txt'

pw.txt                            100%[==========================================================>]      33  --.-KB/s    in 0s      

2025-04-15 20:16:26 (36.5 MB/s) - 'pw.txt' saved [33/33]

Sebas115-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/flag.txt.en
--2025-04-15 20:16:33--  https://mercury.picoctf.net/static/2ac2139344d2e734d5d638ac928f1a8d/flag.txt.en
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 140 [application/octet-stream]
Saving to: 'flag.txt.en'

flag.txt.en                       100%[==========================================================>]     140  --.-KB/s    in 0s      

2025-04-15 20:16:33 (115 MB/s) - 'flag.txt.en' saved [140/140]
```

Después hice un cat al archivo de la contraseña para copiarla: 
```
Sebas115-picoctf@webshell:~$ cat pw.txt 
68f88f9368f88f9368f88f9368f88f93
```

Y finalmente se ejecuta el archivo python con la bandera e introduciendo la contraseña anterior:
```
Sebas115-picoctf@webshell:~$ python ende.py -d flag.txt.en
Please enter the password:68f88f9368f88f9368f88f9368f88f93
picoCTF{4p0110_1n_7h3_h0us3_68f88f93}
```

Flag:
picoCTF{4p0110_1n_7h3_h0us3_68f88f93}
### Notas adicionales

### Referencias
https://webshell.picoctf.org/
