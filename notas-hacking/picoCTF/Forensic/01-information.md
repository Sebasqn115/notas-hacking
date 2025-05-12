### Descripción
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/e5825f58ef798fdd1af3f6013592a971/cat.jpg)

Hints:
1. Look at the details of the file
2. Make sure to submit the flag as picoCTF{XXXXX}

### Solución
Descargamos el archivo cat.
Aplicamos un exiftool para mostrar los metadatos.
Finalmente con exiftool decodificamos en base64 la Licencia para encontrar la bandera:
```
Sebas115-picoctf@webshell:~/forensic$ wget https://mercury.picoctf.net/static/e5825f58ef798fdd1af3f6013592a971/cat.jpg
--2025-05-12 06:32:49--  https://mercury.picoctf.net/static/e5825f58ef798fdd1af3f6013592a971/cat.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 878136 (858K) [application/octet-stream]
Saving to: 'cat.jpg'

cat.jpg                           100%[==========================================================>] 857.55K  1.86MB/s    in 0.4s    

2025-05-12 06:32:49 (1.86 MB/s) - 'cat.jpg' saved [878136/878136]

Sebas115-picoctf@webshell:~/forensic$ exiftool cat.jpg 
ExifTool Version Number         : 12.40
File Name                       : cat.jpg
Directory                       : .
File Size                       : 858 KiB
File Modification Date/Time     : 2021:03:15 18:24:46+00:00
File Access Date/Time           : 2025:05:12 06:32:49+00:00
File Inode Change Date/Time     : 2025:05:12 06:32:49+00:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
Sebas115-picoctf@webshell:~/forensic$ exiftool cat.jpg | grep License
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Sebas115-picoctf@webshell:~/forensic$ exiftool cat.jpg | grep License | sed -e 's/.*: //'
cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Sebas115-picoctf@webshell:~/forensic$ exiftool cat.jpg | grep License | sed -e 's/.*: //' | base64 -d
picoCTF{the_m3tadata_1s_modified}
```

Flag:
picoCTF{the_m3tadata_1s_modified}

### Solución 2
Una forma más simple es decodificar la Licencia que obtuvimos con exiftool aplicando un echo y la decodificación:
```
Sebas115-picoctf@webshell:~/forensic$ echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
picoCTF{the_m3tadata_1s_modified}
```

### Solución 2
Otra sería utilizando Cyberchef:
```
`Input: cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9`
`Recipe: From base64`
`Output: picoCTF{the_m3tadata_1s_modified}`
```
### Notas adicionales


### Referencias
https://gchq.github.io/CyberChef