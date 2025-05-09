### Descripción
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
- [Download compressed disk image](https://artifacts.picoctf.net/c/213/disk.flag.img.gz)

### Solución
Descargar el archivo y observarlo:
Desempaquetar el zip
Aplicar un mms
Luego un fls para buscar directorios
Entrar al del root y ahí se encuentra el archivo flag.txt
El archivo tiene la bandera codificada.
Mandamos eso a otro archivo
Hacemos un icat al history para ver como se encripto y ahora debemos revertir el comando.
Finalmente hacemos un cat al archivo txt que tiene la flag:
```
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ wget [https://artifacts.picoctf.net/c/213/disk.flag.img.gz](https://artifacts.picoctf.net/c/213/disk.flag.img.gz)  
--2025-05-08 14:55:48--  [https://artifacts.picoctf.net/c/213/disk.flag.img.gz](https://artifacts.picoctf.net/c/213/disk.flag.img.gz)  
Resolving [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))... 3.161.55.64, 3.161.55.100, 3.161.55.61, ...  
Connecting to [artifacts.picoctf.net](http://artifacts.picoctf.net/) ([artifacts.picoctf.net](http://artifacts.picoctf.net/))|3.161.55.64|:443... connected.  
HTTP request sent, awaiting response... 200 OK  
Length: 44360922 (42M) [application/octet-stream]  
Saving to: ‘disk.flag.img.gz’  
  
disk.flag.img.gz        100%[============================>]  42.31M  2.88MB/s    in 13s      
  
2025-05-08 14:56:10 (3.16 MB/s) - ‘disk.flag.img.gz’ saved [44360922/44360922]  
  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ gzip -d disk.flag.img.gz  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ ls -lah disk.flag.img  
-rw-rw-r-- 1 kali kali 400M Mar 15  2023 disk.flag.img  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ mmls disk.flag.img    
DOS Partition Table  
Offset Sector: 0  
Units are in 512-byte sectors  
  
      Slot      Start        End          Length       Description  
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)  
001:  -------   0000000000   0000002047   0000002048   Unallocated  
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)  
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)  
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ fls disk.flag.img -o 411648                
d/d 460:        home  
d/d 11: lost+found  
d/d 12: boot  
d/d 13: etc  
d/d 81: proc  
d/d 82: dev  
d/d 83: tmp  
d/d 84: lib  
d/d 87: var  
d/d 96: usr  
d/d 106:        bin  
d/d 120:        sbin  
d/d 466:        media  
d/d 470:        mnt  
d/d 471:        opt  
d/d 472:        root  
d/d 473:        run  
d/d 475:        srv  
d/d 476:        sys  
d/d 2041:       swap  
V/V 51001:      $OrphanFiles  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ fls disk.flag.img -o 411648 472  
r/r 1875:       .ash_history  
r/r * 1876(realloc):    flag.txt  
r/r 1782:       flag.txt.enc  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ icat disk.flag.img -o 411648 1782  
Salted__�ށ��e��B�J▒�c�$QE&$��4jM�KGeE�1�^Ȥ7� ���؎$�'%                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ icat disk.flag.img -o 411648 1782 | file -  
/dev/stdin: openssl enc'd data with salted password  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ icat disk.flag.img -o 411648 1782 > flag.txt.enc  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ icat disk.flag.img -o 411648 1874                
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ icat disk.flag.img -o 411648 1875  
touch flag.txt  
nano flag.txt  
apk get nano  
apk --help  
apk add nano  
nano flag.txt  
openssl  
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567  
shred -u flag.txt  
ls -al  
halt  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ openssl aes256 -salt -d -in flag.txt.enc -out flag.txt unbreakablepassword1234567  
aes256: Extra option: "unbreakablepassword1234567"  
aes256: Use -help for summary.  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567  
*** WARNING : deprecated key derivation used.  
Using -iter or -pbkdf2 would be better.  
bad decrypt  
40475C7C157F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:107:  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567  
*** WARNING : deprecated key derivation used.  
Using -iter or -pbkdf2 would be better.  
bad decrypt  
4087A6AEB87F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:107:  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ ls                                                                                    
disk.flag.img  flag.txt  flag.txt.enc  
                                                                                               
┌──(kali㉿kali)-[~/picoCTF/forensic4/operationorchid]  
└─$ cat flag.txt                                
picoCTF{h4un71ng_p457_5113beab}
```


Flag:
picoCTF{h4un71ng_p457_5113beab}
### Notas adicionales


### Referencias
