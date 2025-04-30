### Descripción
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/d3dd8cd51524d9fafcccd1b7d55f85e7/Forensics%20is%20fun.pptm)
### Solución
Descargar el archivo y observar de que tipo es:

```
┌──(kali㉿kali)-[~/picoCTF/forensic3/macrohardweakedge]
└─$ wget https://mercury.picoctf.net/static/d3dd8cd51524d9fafcccd1b7d55f85e7/Forensics%20is%20fun.pptm
--2025-04-30 00:35:55--  https://mercury.picoctf.net/static/d3dd8cd51524d9fafcccd1b7d55f85e7/Forensics%20is%20fun.pptm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100093 (98K) [application/octet-stream]
Saving to: ‘Forensics is fun.pptm’

Forensics is fun.pptm   100%[=============================>]  97.75K   243KB/s    in 0.4s    

2025-04-30 00:35:56 (243 KB/s) - ‘Forensics is fun.pptm’ saved [100093/100093]

                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/macrohardweakedge]
└─$ ls
'Forensics is fun.pptm'
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/macrohardweakedge]
└─$ file Forensics\ is\ fun.pptm 
Forensics is fun.pptm: Microsoft PowerPoint 2007+
                                                                                              
┌──(kali㉿kali)-[~/picoCTF/forensic3/macrohardweakedge]
└─$ ls -la
total 108
drwxrwxr-x 2 kali kali   4096 Apr 30 00:35  .
drwxrwxr-x 6 kali kali   4096 Apr 30 00:34  ..
-rw-rw-r-- 1 kali kali 100093 Mar 23  2021 'Forensics is fun.pptm'
```

Es un archivo empaquetado, por lo que hay que aplicarle un unzip:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/macrohardweakedge]
└─$ unzip Forensics\ is\ fun.pptm
```

Crear un código con visual code para poder observar de mejor manera las carpetas desempaquetadas y buscar algún archivo:

```
┌──(kali㉿kali)-[~/picoCTF/forensic3/macrohardweakedge]
└─$ code .
```

Aquí se encontró el archivo "hidden" con una cadena en base64, por lo que es necesario convertirla. 
Primero se eliminan los espacios y después se convierte de base64:
```
┌──(kali㉿kali)-[~/picoCTF/forensic3/macrohardweakedge]
└─$ echo "Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q" | tr -d " " | base64 -d
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}
```

Flag:
picoCTF{D1d_u_kn0w_ppts_r_z1p5}
### Notas adicionales


### Referencias
https://docs.fileformat.com/presentation/pptm/