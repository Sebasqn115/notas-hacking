### Descripción
[🥛](http://mercury.picoctf.net:7585/)

Hints:
1. Look at the problem category

### Solución
Dar click en el vaso de leche y observar el código fuente.
La imagen se carga en el .css.
Descargamos la imagen mediante su link.
Instalar zsteg.
Se aplica un export para que no importe el limite del número de carpetas.
Y finalmente se plica un zsteg para observar la bandera:
```
┌──(kali㉿kali)-[~/picoCTF/forensic4/milkslap]
└─$ wget http://mercury.picoctf.net:7585/concat_v.png
--2025-05-09 02:44:21--  http://mercury.picoctf.net:7585/concat_v.png
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:7585... connected.
HTTP request sent, awaiting response... 200 OK
Length: 18095920 (17M) [image/png]
Saving to: ‘concat_v.png’

concat_v.png            100%[============================>]  17.26M  3.19MB/s    in 6.3s    

2025-05-09 02:44:28 (2.72 MB/s) - ‘concat_v.png’ saved [18095920/18095920]

                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/milkslap]
└─$ ls
concat_v.png
                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/milkslap]
└─$ export RUBY_THREAD_VM_STACK_SIZE=500000000
                                                                                             
┌──(kali㉿kali)-[~/picoCTF/forensic4/milkslap]
└─$ zsteg -a concat_v.png 

imagedata           .. text: "\n\n\n\n\n\n\t\t"
b1,b,lsb,xy         .. text: "picoCTF{imag3_m4n1pul4t10n_sl4p5}\n"
b1,bgr,lsb,xy       .. /var/lib/gems/3.1.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect': stack level too deep (SystemStackError)
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
        from /var/lib/gems/3.1.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
         ... 4807703 levels...
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
        from /var/lib/gems/3.1.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
        from /usr/local/bin/zsteg:25:in `load'
        from /usr/local/bin/zsteg:25:in `<main>'
```

Flag:
picoCTF{imag3_m4n1pul4t10n_sl4p5}
### Notas adicionales


### Referencias
