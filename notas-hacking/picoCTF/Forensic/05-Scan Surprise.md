### Descripción
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/16/challenge.zip)

The same files are accessible via SSH here:`ssh -p 59382 ctf-player@atlas.picoctf.net`Using the password `6abf4a82`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

Hints:
1. QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
2. Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
3. If you don't have access to a phone, you can also use zbar-tools to convert an image to text

### Solución
Descargamos el archivo .zip.
Lo descomprimimos.
Vamos entrando a los directorios hasta encontrar una imagen.
La abrimos y observamos un código QR que al escanearse nos da la bandera.
```
Sebas115-picoctf@webshell:~/forensic$ wget https://artifacts.picoctf.net/c_atlas/16/challenge.zip
--2025-05-12 07:10:59--  https://artifacts.picoctf.net/c_atlas/16/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.92, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 736 [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                     100%[==========================================================>]     736  --.-KB/s    in 0s      

2025-05-12 07:10:59 (153 MB/s) - 'challenge.zip' saved [736/736]

Sebas115-picoctf@webshell:~/forensic$ ls
challenge.zip

Sebas115-picoctf@webshell:~/forensic$ unzip challenge.zip 
Archive:  challenge.zip
   creating: home/ctf-player/drop-in/
 extracting: home/ctf-player/drop-in/flag.png  
Sebas115-picoctf@webshell:~/forensic$ ls
challenge.zip  home
Sebas115-picoctf@webshell:~/forensic$ cd home/
Sebas115-picoctf@webshell:~/forensic/home$ ls
ctf-player
Sebas115-picoctf@webshell:~/forensic/home$ cd ctf-player/
Sebas115-picoctf@webshell:~/forensic/home/ctf-player$ ls
drop-in
Sebas115-picoctf@webshell:~/forensic/home/ctf-player$ cd drop-in/
Sebas115-picoctf@webshell:~/forensic/home/ctf-player/drop-in$ ls
flag.png
Sebas115-picoctf@webshell:~/forensic/home/ctf-player/drop-in$ cat flag.png 
PNG

IHDRcc,PLTEٟtRNSȵ       pHYs

                            ~IDAT81 
ɮ`g 8u=֪AzsVv)gfaδ<;xER>pЉ           PG@5ظ\ 4HĖk qe@r4]QLy       ?!D
                         NNDqGjI\8,+-lSפ^YIȉN޳hv͵DN۾4ryҲ79⑶ %Pz+JI}⽲
IENDB`
```


Flag:
picoCTF{p33k_@_b00_7843f77c}
### Notas adicionales
Se escanea un QR, en este caso se hizo con la camara del celular por practicidad.

### Referencias
