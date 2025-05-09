### Descripción
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz)

Hints:
1. Have you ever used `file` to determine what a file was?
2. Relevant terminal-fu in picoGym: https://play.picoctf.org/practice/challenge/85
3. Mastering this terminal-fu would enable you to find the flag in a single command: https://play.picoctf.org/practice/challenge/48
4. Using your own computer, you could use qemu to boot from this disk!

### Solución
Descargar el archivo y observarlo:
Desempaquetar el zip.
Aplicar un file a la imagen.
Aplicar el comando srch_strings con grep a la imagen para obtener la bandera: 
```
┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ wget https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz
--2025-05-09 02:40:53--  https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29768911 (28M) [application/octet-stream]
Saving to: ‘dds1-alpine.flag.img.gz’

dds1-alpine.flag.img.gz 100%[============================>]  28.39M  2.02MB/s    in 19s     

2025-05-09 02:41:12 (1.52 MB/s) - ‘dds1-alpine.flag.img.gz’ saved [29768911/29768911]

                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ ls
dds1-alpine.flag.img.gz
                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ gzip -d dds1-alpine.flag.img.gz 
                                                                                             

┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ 
                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ ls
dds1-alpine.flag.img
                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ ls -la
total 131080
drwxrwxr-x 2 kali kali      4096 May  9 02:41 .
drwxrwxr-x 7 kali kali      4096 May  8 15:13 ..
-rw-rw-r-- 1 kali kali 134217728 Mar 15  2021 dds1-alpine.flag.img
                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ file dds1-alpine.flag.img 
dds1-alpine.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0x10,81,1), startsector 2048, 260096 sectors
                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/diskdisksleuth]
└─$ srch_strings dds1-alpine.flag.img | grep pico         
ffffffff81399ccf t pirq_pico_get
ffffffff81399cee t pirq_pico_set
ffffffff820adb46 t pico_router_probe
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_267e38f6}
```


Flag:
picoCTF{f0r3ns1c4t0r_n30phyt3_267e38f6}
### Notas adicionales


### Referencias
