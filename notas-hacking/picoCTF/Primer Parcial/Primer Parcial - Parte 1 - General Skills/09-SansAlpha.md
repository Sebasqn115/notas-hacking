### Descripción
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.`ssh -p 61413 ctf-player@mimas.picoctf.net`Use password: `6dd28e9b`

Hints:
1. Where can you get some letters?

### Solución
Entramos al servidor e introducimos la contraseña:

```
Sebas115-picoctf@webshell:~$ ssh -p 61413 ctf-player@mimas.picoctf.net
The authenticity of host '[mimas.picoctf.net]:61413 ([52.15.88.75]:61413)' can't be established.
ED25519 key fingerprint is SHA256:n/hDgUtuTTF85Id7k2fxmHvb6rrLrACHNM6xLZ46AqQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[mimas.picoctf.net]:61413' (ED25519) to the list of known hosts.
ctf-player@mimas.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1016-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable
```

Buscamos los caracteres necesarios en https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm:
```
SansAlpha$ /*
bash: /bin: Is a directory

SansAlpha$ /*/???
E: Invalid operation /bin/awk

SansAlpha$ /*/??????
/bin/base32: extra operand ‘/bin/base64’
Try '/bin/base32 --help' for more information.

SansAlpha$ /*/????64 */*
/bin/base64: extra operand ‘/bin/x86_64’
Try '/bin/base64 --help' for more information.

SansAlpha$ /*/???[!_]64 */*
/bin/base64: extra operand ‘blargh/flag.txt’
Try '/bin/base64 --help' for more information.

SansAlpha$ /*/???[!_]64 */????.*
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV8xNDUyNTZlY30=
```

Aquí lo que se hace es entrar a un entorno personalizado SansAlpha$ por lo que los comandos de la página (comodines) no son de ayuda para buscar archivos o comandos con información importante.
/ --> es el directorio raíz.
???, ??????, ???[!_]64 --> ayudan a filtrar nombres de archivo.

Al final se nos muestra un archivo que viene codificado en base64, para el cual nos salimos del entorno personalizado para hacer un echo y decodificarlo en base64:
```
SansAlpha$ exit
Connection to mimas.picoctf.net closed.
Sebas115-picoctf@webshell:~$ echo cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV8xNDUyNTZlY30= | base64 -d
return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_145256ec}
```

Flag:
picoCTF{7h15_mu171v3r53_15_m4dn355_145256ec}
### Notas adicionales

### Referencias
https://webshell.picoctf.org/
