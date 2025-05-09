### Descripción
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/136/disk.flag.img.gz)

### Solución
Descargar los archivos y observarlos.
Descomprimir el archivo.
Observar sus características.
Ver las particiones.
Usar fls con el comienzo de la partición
Usar icat para ver el archivo de la flag encontrado.

```
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ wget [https://artifacts.picoctf.net/c/136/disk.flag.img.gz](https://artifacts.picoctf.net/c/136/disk.flag.img.gz)  
--2025-05-08 14:41:14--  [https://artifacts.picoctf.net/c/136/disk.flag.img.gz](https://artifacts.picoctf.net/c/136/disk.flag.img.gz)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.64, 3.161.55.26, 3.161.55.100, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.64|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 47534571 (45M) [application/octet-stream]  
Saving to: ‘disk.flag.img.gz’  
  
disk.flag.img.gz        100%[============================>]  45.33M  1.43MB/s    in 34s      
  
2025-05-08 14:41:57 (1.35 MB/s) - ‘disk.flag.img.gz’ saved [47534571/47534571]  
  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ gzip -d disk.flag.img.gz  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ ls -lag disk.flag.img  
-rw-rw-r-- 1 kali 314572800 Mar 15  2023 disk.flag.img  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ srch_strings disk.flag.img | grep pico  
ffffffff816989a0 t pirq_pico_get  
ffffffff816989c0 t pirq_pico_set  
ffffffff824640e2 t pico_router_probe  
  
application/x-sega-pico-rom  
picoJava,  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ mmls disk.flag.img                                          
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)  
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)  
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ fls disk.flag.img -o 360448  
d/d 451:        home  
d/d 11: lost+found  
d/d 12: boot  
d/d 1985:       etc  
d/d 1986:       proc  
d/d 1987:       dev  
d/d 1988:       tmp  
d/d 1989:       lib  
d/d 1990:       var  
d/d 3969:       usr  
d/d 3970:       bin  
d/d 1991:       sbin  
d/d 1992:       media  
d/d 1993:       mnt  
d/d 1994:       opt  
d/d 1995:       root  
d/d 1996:       run  
d/d 1997:       srv  
d/d 1998:       sys  
d/d 2358:       swap  
V/V 31745:      $OrphanFiles  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ fls disk.flag.img -o 360448 -r | grep flag  
++ r/r * 2082(realloc): flag.txt  
++ r/r 2371:    flag.uni.txt  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitapprentice]  
└─$ icat disk.flag.img -o 360448 2371  

picoCTF{by73_5urf3r_3497ae6b}
```


Flag:
picoCTF{by73_5urf3r_3497ae6b}
### Notas adicionales


### Referencias
