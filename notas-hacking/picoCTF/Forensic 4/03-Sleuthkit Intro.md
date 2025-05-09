### Descripción
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.[Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)Access checker program: `nc saturn.picoctf.net 53917`

### Solución
Descargar el archivo y observarlo:
Descomprimir el zip
Ver las particiones
Lanzar la instancia y conectarnos a el link
Y al introducir el tamaño de la partición nos manda la bandera:

```
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitintro]  
└─$ wget [https://artifacts.picoctf.net/c/164/disk.img.gz](https://artifacts.picoctf.net/c/164/disk.img.gz)  
--2025-05-08 14:33:49--  [https://artifacts.picoctf.net/c/164/disk.img.gz](https://artifacts.picoctf.net/c/164/disk.img.gz)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.100, 3.161.55.26, 3.161.55.64, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.100|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 29714372 (28M) [application/octet-stream]  
Saving to: ‘disk.img.gz’  
  
disk.img.gz             100%[============================>]  28.34M  1.97MB/s    in 25s      
  
2025-05-08 14:34:23 (1.16 MB/s) - ‘disk.img.gz’ saved [29714372/29714372]  
  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitintro]  
└─$ gzip -d disk.img.gz  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitintro]  
└─$ ls  
disk.img  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitintro]  
└─$ ls -lah disk.img  
-rw-rw-r-- 1 kali kali 100M Aug  4  2023 disk.img  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitintro]  
└─$ mmls disk.img                                          
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/sleuthkitintro]  
└─$ nc [saturn.picoctf.net](http://saturn.picoctf.net/) 53917  
What is the size of the Linux partition in the given disk image?  
Length in sectors: 0000202752  
0000202752  
Great work!  
picoCTF{mm15_f7w!}
```


Flag:
picoCTF{mm15_f72!}
### Notas adicionales


### Referencias
