### Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.

Hints:
1. Try using a tool like Wireshark
2. What are streams?

### Solución
Primero se descarga el archivo:
```
┌──(kali㉿kali)-[~/picoCTF/forensic/sharkonwire1]
└─$ wget https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
--2025-04-01 19:12:01--  https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 239455 (234K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap          100%[======================>] 233.84K   773KB/s    in 0.3s    

2025-04-01 19:12:01 (773 KB/s) - ‘capture.pcap’ saved [239455/239455]

┌──(kali㉿kali)-[~/picoCTF/forensic/sharkonwire1]
└─$ ls
capture.pcap
                                                                                     
┌──(kali㉿kali)-[~/picoCTF/forensic/sharkonwire1]
└─$ file capture.pcap 
capture.pcap: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)
```

Después se utiliza la herramienta Wireshark, se abre el archivo que descargamos y se busca busca un protocolo UDP al cual se le hace un follow y en el canal 6 se encuentra la bandera:
```
picoCTF{StaT31355_636f6e6e}
```

Flag:
picoCTF{StaT31355_636f6e6e}

### Notas adicionales


### Referencias
Herramienta Wireshark
