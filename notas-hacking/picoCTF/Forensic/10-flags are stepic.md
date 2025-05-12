### Descripción
A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their messageTry it [here](http://standard-pizzas.picoctf.net:59043/)!

Hints:
1. In the country that doesn't exist, the flag persists

### Solución
Entramos a la página que nos da: http://standard-pizzas.picoctf.net:59043/.
Ubicamos que el país que no existe es Upanzi.
Descargamos esa imagen.
Utilizamos la herramienta stepic para decodificar la imagen.


```
┌──(kali㉿kali)-[~/picoCTF/forensic]  
└─$ wget [http://standard-pizzas.picoctf.net:58266/flags/upz.png](http://standard-pizzas.picoctf.net:58266/flags/upz.png)  
--2025-05-12 04:04:50--  [http://standard-pizzas.picoctf.net:58266/flags/upz.png](http://standard-pizzas.picoctf.net:58266/flags/upz.png)  
Resolving [standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/) ([standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/))... 3.22.195.189  
Connecting to [standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/) ([standard-pizzas.picoctf.net](http://standard-pizzas.picoctf.net/))|3.22.195.189|:58266... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 1788398 (1.7M) [image/png]  
Saving to: ‘upz.png’  
  
upz.png                 100%[============================>]   1.71M  1.64MB/s    in 1.0s      
  
2025-05-12 04:04:51 (1.64 MB/s) - ‘upz.png’ saved [1788398/1788398]

┌──(kali㉿kali)-[~/picoCTF/forensic]  
└─$ ls  
upz.png  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic]  
└─$ exiftool upz.png                
ExifTool Version Number         : 13.00  
File Name                       : upz.png  
Directory                       : .  
File Size                       : 1788 kB  
File Modification Date/Time     : 2025:03:05 22:59:01-05:00  
File Access Date/Time           : 2025:05:12 04:04:51-04:00  
File Inode Change Date/Time     : 2025:05:12 04:04:51-04:00  
File Permissions                : -rw-rw-r--  
File Type                       : PNG  
File Type Extension             : png  
MIME Type                       : image/png  
Image Width                     : 14173  
Image Height                    : 10630  
Bit Depth                       : 8  
Color Type                      : RGB with Alpha  
Compression                     : Deflate/Inflate  
Filter                          : Adaptive  
Interlace                       : Noninterlaced  
Image Size                      : 14173x10630  

Megapixels                      : 150.7

┌──(kali㉿kali)-[~/picoCTF/forensic]  
└─$ stepic -i upz.png -d  
/usr/lib/python3/dist-packages/PIL/Image.py:3368: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.  
  warnings.warn(  
picoCTF{fl4g_h45_fl4g1a2a9157}
```


Flag:
picoCTF{fl4g_h45_fl4g1a2a9157}
### Notas adicionales


### Referencias
