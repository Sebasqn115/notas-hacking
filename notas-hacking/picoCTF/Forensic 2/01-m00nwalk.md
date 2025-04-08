### Descripción
Decode this [message](https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav) from the moon.

Hints:
1. How did pictures from the moon landing get sent back to Earth?
2. What is the CMU mascot?, that might help select a RX option

### Solución
Primero se descarga el archivo:
```
┌──(kali㉿kali)-[~/picoCTF/forensic/m00nwalk]
└─$ wget https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav
--2025-04-08 12:07:28--  https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11066998 (11M) [application/octet-stream]
Saving to: ‘message.wav’

message.wav           100%[======================>]  10.55M  1.91MB/s    in 5.1s    

2025-04-08 12:07:33 (2.07 MB/s) - ‘message.wav’ saved [11066998/11066998]
```

Después, se instala el repo con la herramienta de decodificación SSTV y sus paquetes.
```
┌──(kali㉿kali)-[/opt]
└─$ sudo git clone https://github.com/colaclanth/sstv.git
[sudo] password for kali: 
Cloning into 'sstv'...
remote: Enumerating objects: 221, done.
remote: Counting objects: 100% (59/59), done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 221 (delta 51), reused 49 (delta 49), pack-reused 162 (from 1)
Receiving objects: 100% (221/221), 1.01 MiB | 2.04 MiB/s, done.
Resolving deltas: 100% (139/139), done.

┌──(kali㉿kali)-[/opt/sstv]
└─$ sudo python3 setup.py install                        
running install
/usr/lib/python3/dist-packages/setuptools/_distutils/cmd.py:66: SetuptoolsDeprecationWarning: setup.py install is deprecated. Using /usr/lib/python3/dist-packages
Finished processing dependencies for sstv==0.1
```

Se aplica la herramienta al archivo .wav que descargamos.
```
┌──(kali㉿kali)-[~/picoCTF/forensic2/forensic/m00nwalk]
└─$ sstv -d message.wav -o result.png
[sstv] Searching for calibration header... Found!    
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [###################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```

Y ahora abrimos la imagen creada al usar la herramienta:
```
┌──(kali㉿kali)-[~/picoCTF/forensic2/forensic/m00nwalk]
└─$ open result.png
```

En la imagen observamos se puede ver la bandera, solo hace falta rotarla para una mejor visualización.
Flag:
picoCTF{beep_boop_im_in_space}

### Notas adicionales


### Referencias
Herramienta para decodificar sstv.
