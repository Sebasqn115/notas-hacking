### Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.

Hints:
1. Try using a tool like Wireshark.
2. How can you decrypt the TLS stream?

### Solución
Descargar los archivos y observarlos:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3]
└─$ wget https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap
--2025-04-29 15:58:02--  https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13163 (13K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap            100%[=============================>]  12.85K  --.-KB/s    in 0s      

2025-04-29 15:58:02 (576 MB/s) - ‘capture.pcap’ saved [13163/13163]

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3]
└─$ wget https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key
--2025-04-29 15:58:09--  https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1704 (1.7K) [application/octet-stream]
Saving to: ‘picopico.key’

picopico.key            100%[=============================>]   1.66K  --.-KB/s    in 0s      

2025-04-29 15:58:10 (82.3 MB/s) - ‘picopico.key’ saved [1704/1704]

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3]
└─$ ls -la
total 28
drwxrwxr-x 2 kali kali  4096 Apr 29 15:58 .
drwxrwxr-x 6 kali kali  4096 Apr 29 15:54 ..
-rw-rw-r-- 1 kali kali 13163 Oct 26  2020 capture.pcap
-rw-rw-r-- 1 kali kali  1704 Oct 26  2020 picopico.key
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3]
└─$ file capture.pcap 
capture.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 65535)
```

Abrir la captura con wireshark:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3]
└─$ wireshark capture.pcap 
Warning: program compiled against libxml 212 using older 209
```

Se usa la llave para desencriptar la captura de paquetes.
Se abre la captura de paquetes con wireshark
Cargar la llave privada en Edicion  --> Preferencias --> Protocolos --> TLS --> Cargar llave RSA.
Después buscar la cadena picoCTF y ahora si podemos encontrar la bandera:
```
Pico-Flag: picoCTF{nongshim.shrimp.crackers}
```

Flag:
picoCTF{nongshim.shrimp.crackers}
### Notas adicionales


### Referencias
