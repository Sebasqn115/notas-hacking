### Descripción
Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/476/enc_flag).

Hints:
1. Multiple decoding is always good.

### Solución
Con Python

```
Sebas115-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/476/enc_flag
--2025-02-18 18:57:11--  https://artifacts.picoctf.net/c/476/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.92, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 349 [application/octet-stream]
Saving to: 'enc_flag'

enc_flag                       100%[====================================================>]     349  --.-KB/s    in 0s      

2025-02-18 18:57:12 (24.5 MB/s) - 'enc_flag' saved [349/349]

Sebas115-picoctf@webshell:~$ cat enc_flag 
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKVVZXMTRWMDVHV2toalJYUlhDazFyV25sVVZXaHpWakpHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==
Sebas115-picoctf@webshell:~$ cat enc_flag | base64 -d
VjFSQ2EyTXlSblJUV0dSVllrWmFWRmx0TlZOalJtUlhZVVU1YVZKVVZuaFdWekZoWVZkR2NrNVVX
bUZTVmtwUVdWUkdibVZXVm5WUgpiSEJzWVRCd2VWVXhXbXBOUlRWSFdqTnNWZ3BYUjFKeVZGZHdW
MlZzVWxaVmJFNW9UVVJDTlZaWE1XRlVkM0JUVW14V05GWkhjRXRXCk1rWnlUVWhzVjJGdGVFVlhi
bTkzVDFWT2JsQlVNRXNLCg==
Sebas115-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d
V1RCa2MyRnRTWGRVYkZaVFltNVNjRmRXYUU5aVJUVnhWVzFhYVdGck5UWmFSVkpQWVRGbmVWVnVR
bHBsYTBweVUxWmpNRTVHWjNsVgpXR1JyVFdwV2VsUlZVbE5oTURCNVZXMWFUd3BTUmxWNFZHcEtW
MkZyTUhsV2FteEVXbm93T1VOblBUMEsK
Sebas115-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d
WTBkc2FtSXdUbFZTYm5ScFdWaE9iRTVxVW1aaWFrNTZaRVJPYTFneVVuQlpla0pyU1ZjME5GZ3lV
WGRrTWpWelRVUlNhMDB5VW1aTwpSRlV4VGpKV2FrMHlWamxEWnowOUNnPT0K
Sebas115-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d | base64 -d
Y0dsamIwTlVSbnRpWVhObE5qUmZiak56ZEROa1gyUnBZekJrSVc0NFgyUXdkMjVzTURSa00yUmZO
RFUxTjJWak0yVjlDZz09Cg==
Sebas115-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
cGljb0NURntiYXNlNjRfbjNzdDNkX2RpYzBkIW44X2Qwd25sMDRkM2RfNDU1N2VjM2V9Cg==
Sebas115-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d 

picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_4557ec3e}

```

Se descodifica con base64 6 veces el archivo para llegar a la flag. Esto depende de lo que nos vaya arrojando tras cada descodificación.

picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_4557ec3e}

### Solución 2
Otra solucion es con cyberchef pasando 6 veces por From Base64.
Usando cyberchef https://gchq.github.io/CyberChef

```
`Input: VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKVVZXMTRWMDVHV2toalJYUlhDazFyV25sVVZXaHpWakpHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==`
`Recipe: From base64`
`Recipe: From base64`
`Recipe: From base64`
`Recipe: From base64`
`Recipe: From base64`
`Recipe: From base64`
`Output: picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_4557ec3e}`
```


### Notas adicionales


### Referencias
https://webshell.picoctf.org/
https://gchq.github.io/CyberChef
