### Descripción
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap) and try to get the flag.

Hints:
1. Filter your packets to narrow down your search.
2. Attacks were done in timely manner.
3. Time is essential

### Solución
Descargamos el archivo .pcap.
Utilizamos la herramienta tshark para archivo de datos con algunos filtros -Y como paquetes tcp de longitud=12 o longitud=4, el tiempo, los datos organizados, tomamos los datos de la última columna en hexadecimal y en el mismo comando decodificamos la cadena en base64.
```
Sebas115-picoctf@webshell:~/forensic$ wget https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap
--2025-05-12 07:43:10--  https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.95, 3.160.5.18, 3.160.5.40, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.95|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1452 (1.4K) [application/octet-stream]
Saving to: 'myNetworkTraffic.pcap'

myNetworkTraffic.pcap             100%[==========================================================>]   1.42K  --.-KB/s    in 0s      

2025-05-12 07:43:11 (1.26 GB/s) - 'myNetworkTraffic.pcap' saved [1452/1452]

Sebas115-picoctf@webshell:~/forensic$ exiftool myNetworkTraffic.pcap 
ExifTool Version Number         : 12.40
File Name                       : myNetworkTraffic.pcap
Directory                       : .
File Size                       : 1452 bytes
File Modification Date/Time     : 2025:03:06 03:31:41+00:00
File Access Date/Time           : 2025:05:12 07:43:11+00:00
File Inode Change Date/Time     : 2025:05:12 07:43:11+00:00
File Permissions                : -rw-rw-r--
Error                           : Unknown file type
Sebas115-picoctf@webshell:~/forensic$ ls
myNetworkTraffic.pcap

Sebas115-picoctf@webshell:~/forensic$ tshark -r myNetworkTraffic.pcap -Y "tcp.len==12 || tcp.len==4" -T fields -e frame.time -e tcp.segment_data | sort -k4 | awk '{print $6}' | xxd -p -r | base64 -d
picoCTF{1t_w4snt_th4t_34sy_tbh_4r_959f50d3}

```

Flag:
picoCTF{1t_w4snt_th4t_34sy_tbh_4r_959f50d3}
### Notas adicionales


### Referencias
