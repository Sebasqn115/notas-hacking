### Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.

Hints:
1. Try using a tool like Wireshark.
2. How can you decrypt the TLS stream?

### Solución
Descargar archivos:

```
┌──(kali㉿kali)-[~/picoCTF/forensic3/webnet1]
└─$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap
--2025-04-29 16:12:46--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92525 (90K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap            100%[=============================>]  90.36K  --.-KB/s    in 0.1s    

2025-04-29 16:12:47 (843 KB/s) - ‘capture.pcap’ saved [92525/92525]

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/webnet1]
└─$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
--2025-04-29 16:12:59--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1704 (1.7K) [application/octet-stream]
Saving to: ‘picopico.key’

picopico.key            100%[=============================>]   1.66K  --.-KB/s    in 0s      

2025-04-29 16:12:59 (72.6 MB/s) - ‘picopico.key’ saved [1704/1704]

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/webnet1]
└─$ ls
capture.pcap  picopico.key
```

Abrir la captura con wireshark:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/webnet1]
└─$ wireshark capture.pcap 
Warning: program compiled against libxml 212 using older 209
```

Cargar la llave y observar que en el paquete 47 se encuentra una imagen que se está descargando por lo que hay que extraerla del trafico con export objects --> HTTP --> grabarla al disco --> examinarla
Abrir la imagen con:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/webnet1]
└─$ ls  
capture.pcap  picopico.key  vulture.jpg
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/webnet1]
└─$ open vulture.jpg
```


Aplicar un strings:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/webnet1]
└─$ strings vulture.jpg -n15
picoCTF{honey.roasted.peanuts}
 )/'%'/9339GDG]]}
 )/'%'/9339GDG]]}
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
```

Flag:
picoCTF{honey.roasted.peanuts}
### Notas adicionales


### Referencias
